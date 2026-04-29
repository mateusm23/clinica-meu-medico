# Módulo Financeiro — Clínica Meu Médico

Sistema integrado de conciliação bancária desenvolvido em HTML/JS puro (sem backend).
Arquivo principal: `financeiro.html`

---

## O que o módulo faz

O cliente recebia extratos bancários de 3 contas + relatório do ERP de consultas todo mês e precisava:
- Copiar os dados manualmente para o Excel
- Montar tabelas dinâmicas
- Classificar cada lançamento por categoria de custo
- Conferir saldos entre o que entrou/saiu nos extratos vs. o que o ERP registrou

O módulo automatiza a leitura e unificação dos extratos, gera a planilha base já formatada com fórmulas e validações, e o usuário só precisa preencher a coluna **ALOCAÇÃO** (categoria de cada lançamento).

---

## Arquitetura

100% frontend — HTML + JavaScript rodando no navegador.
Nenhum dado sai da máquina do usuário.

Bibliotecas:
- **SheetJS (xlsx@0.18.5)** — leitura dos `.xls`/`.xlsx` de entrada
- **ExcelJS (exceljs@4.4.0)** — geração do Excel de saída formatado

---

## Fontes de dados suportadas

| Slot | Banco | Formato |
|------|-------|---------|
| 1 | Valori Bank KS | `.xls` — colunas: Data Referência, Hora, Tipo, Descrição, Valor, D/C, Saldo |
| 2 | Valori Bank MM | `.xls` — mesmo formato do KS |
| 3 | Santander | `.xlsx` — colunas: Data, Histórico, Documento, Valor, Saldo |
| 4 | ERP de Consultas | `.xlsx` — relatório nativo do sistema, 5 linhas de cabeçalho, dados a partir da linha 6 |

O ERP é **informacional** — não tem relação 1:1 com os extratos bancários.
Registros ERP representam consultas individuais (pacientes/médicos), não transações financeiras.

---

## Lógica de parsing

### Valori KS / MM
- Ignora linhas com tipo "Saldo do dia"
- Coluna D/C: `C` → Entrada, `D` → Saída
- Condição derivada do campo Tipo: PIX / BOLETO / CARTÃO CRÉDITO / CARTÃO DÉBITO / DEPÓSITO / TARIFA / TED/DOC / SAQUE / OUTROS

### Santander
- Detecta início dos dados procurando a linha com célula `data` nas primeiras 6 linhas
- Valor positivo → Entrada, negativo → Saída
- Condição derivada do campo Histórico: PIX / CARTÃO / BOLETO / TARIFA / TED/DOC / DARF / COBRANÇA

### Detecção automática de formato
`detectAndParse()` olha a primeira célula do arquivo:
- `AGENCIA` → Santander
- `DATA REFERÊNCIA` ou headers com `D/C` → Valori

### ERP — campo DOC CORRIGIDO
Lógica de negócio específica do cliente:
```
if (profissional inclui "CIMRAD" && documento == "Outros") → "Cimrad"
if (profissional inclui "CENTER X" && documento == "Outros") → "Center X"
if (conta_bancaria inclui "SICOOB") → "SICOOB"
senão → documento original
```
Cimrad e Center X são máquinas de cartão parceiras que aparecem no ERP mas não nos extratos bancários.

---

## Deduplicação

Chave única por transação:
```
BANCO|DD/MM/YYYY|valor_abs_2dec|desc[0:40]
```

Os primeiros 40 caracteres da descrição evitam colisão entre a linha principal de um PIX e a linha de tarifa do PIX (mesmo dia, mesmo banco, mas valores diferentes).

Transações duplicadas são marcadas com `duplicata: true` e destacadas na tabela de preview.

---

## Plano de Contas

Gerenciado dentro da própria página (sem backend).
Persiste em `localStorage` com a chave `clinica_plano_contas`.

Cada categoria tem:
- **REF** — código numérico (ex: `1.1`, `4.5`)
- **CUSTO** — `FIXO` ou `VARIAVEL`
- **DISCRIMINAÇÃO** — nome do item de custo (ex: `AGUA E ESGOTO`)
- **CATEGORIA** — grupo (ex: `DESPESAS ADMINISTRATIVAS`)
- **CHAVE** — concatenação dos 4 campos, usada como identificador único no dropdown do Excel

O usuário pode adicionar, editar e remover categorias via modal.
Botão "Restaurar Padrão" volta para os 28 itens originais.

---

## Planilha Excel gerada

### Aba LISTAS
Todas as categorias do Plano de Contas.
Usada como fonte dos dropdowns e fórmulas na aba APURAÇÃO.

| Coluna | Campo |
|--------|-------|
| A | REF |
| B | CUSTO |
| C | DISCRIMINAÇÃO |
| D | CATEGORIA |
| E | CHAVE (chave completa, usada nos MATCH) |

### Aba APURAÇÃO
Lançamentos bancários, ordenados por data crescente.
Linha 1 congelada, filtro automático.

| Col | Campo | Conteúdo |
|-----|-------|----------|
| A | DT PGTO | Data da transação (DD/MM/YYYY) |
| B | FORMA | Nome do banco |
| C | CONDIÇÃO | PIX / BOLETO / CARTÃO / etc. |
| D | PARCELA | Sempre "N/A" |
| E | PRESTADOR / COLABORADOR | Descrição do extrato |
| F | ALOCAÇÃO | **Usuário preenche** — dropdown com CHAVEs do Plano de Contas |
| G | CUSTO | `=IFERROR(INDEX(LISTAS!$B:$B,MATCH($F2,LISTAS!$E:$E,0)),"")` |
| H | DISCRIMINAÇÃO | `=IFERROR(INDEX(LISTAS!$C:$C,MATCH($F2,LISTAS!$E:$E,0)),"")` |
| I | CATEGORIA | `=IFERROR(INDEX(LISTAS!$D:$D,MATCH($F2,LISTAS!$E:$E,0)),"")` |
| J | ENTRADA | Valor se tipo=Entrada, vazio se Saída |
| K | SAÍDA | Valor se tipo=Saída, vazio se Entrada |
| L | COMPROVANTE / RECIBO | **Usuário preenche** — link ou número do comprovante |
| M | MÊS | Formato `03 MAR - 26` |
| N | TOTAL | `=IF(J2>0,J2,K2)` |

Fórmulas G/H/I usam apenas INDEX+MATCH e IFERROR — compatíveis com Excel 2016/2019.
Sem fórmulas dinâmicas (UNIQUE, FILTER, XLOOKUP, etc.).

**Formatação condicional (prioridade 1 = mais alta):**
1. ALOCAÇÃO vazia → fundo **amarelo** (sinaliza que precisa preencher)
2. Linha de Entrada → fundo **verde claro**
3. Linha de Saída → fundo **rosa claro**

Quando o usuário preenche a ALOCAÇÃO, o amarelo some e a cor de entrada/saída aparece.

### Aba ERP
Exibida apenas se o arquivo ERP foi carregado.
9 colunas simplificadas (o relatório original tem 24).

| Coluna | Campo |
|--------|-------|
| A | CONTA BANCÁRIA |
| B | CAT. FATURAMENTO |
| C | CLIENTE / FORNECEDOR |
| D | PAGAMENTO (DD/MM/YYYY) |
| E | DOC CORRIGIDO |
| F | PROFISSIONAL |
| G | VALOR |
| H | DESCONTO |
| I | TOTAL |

---

## Formato do MÊS

```
03 MAR - 26
^^ ^^^   ^^
MM MES   YY (2 últimos dígitos do ano)
```

---

## Fases de desenvolvimento

| Fase | O que foi feito | Status |
|------|-----------------|--------|
| 1 | Parsers de extrato, pipeline de deduplicação, preview em tabela | Concluído |
| 2 | Plano de Contas com localStorage, modal add/edit | Concluído |
| 3 | Geração do Excel (LISTAS + APURAÇÃO + ERP) com ExcelJS | Concluído |
| 4 | Aba RESUMO + FLUXO DE CAIXA (SUMIFS por categoria/mês) | Pendente |
| 5 | Aba CONFERÊNCIA DE SALDOS | Pendente |
| 6 | Merge incremental (ler Excel anterior, preservar ALOCAÇÃO preenchida, adicionar novas linhas) | Pendente |

---

## Restrições técnicas

- Nunca usar fórmulas dinâmicas do Excel 365 (UNIQUE, FILTER, IFS/SES, XLOOKUP/PROCX, SEQUENCE). O cliente usa Excel 2016/2019.
- Fórmulas permitidas: SUMIFS, SUMIF, VLOOKUP/PROCV, IF/SE, IFERROR/SEERRO, COUNTIFS, INDEX, MATCH.
- CAIXA INTERNO (caixa físico da clínica) não tem extrato bancário — entrada manual no Excel pelo próprio usuário.

---

## Arquivos de exemplo

Estão em `exemplos/` (não versionados no git por conter dados reais):
- `EXTRATO - VALORI KS.xls` — 195 linhas
- `EXTRATO - VALORI MM.xls` — 367 linhas
- `EXTRATO - SANTANDER.xlsx` — 158 linhas
- `Relatorio_Financeiro_Geral (RELATORIO NATIVO DO ERP DE CONSULTAS).xlsx` — 2659 registros
