# 🏥 Clínica Meu Médico - Portal de Automações

Sistema de automações financeiras e operacionais desenvolvido em HTML/JS puro (100% no navegador, sem servidor).

## 🚀 Demo ao Vivo

👉 **[Acesse o Sistema](https://mateusm23.github.io/clinica-meu-medico/)**

---

## 🎯 Módulos

### ✅ Módulo Financeiro (`financeiro.html`)
Mini sistema integrado de conciliação bancária mensal.

- Upload de extratos bancários: **Valori KS**, **Valori MM**, **Santander**
- Upload do relatório ERP de consultas (opcional, informacional)
- Detecção automática de formato de cada banco
- Deduplicação de lançamentos por chave única
- Plano de Contas gerenciável (localStorage) com 28 categorias padrão
- Preview interativo com filtros por tipo e busca por descrição
- **Geração de Excel** com 3 abas:
  - **LISTAS** — Plano de Contas completo (fonte dos dropdowns)
  - **APURAÇÃO** — Lançamentos com fórmulas INDEX/MATCH, dropdown de ALOCAÇÃO e formatação condicional
  - **ERP** — 9 colunas simplificadas do relatório de consultas
- Fórmulas compatíveis com Excel 2016/2019

### ✅ Portal de Parceiros (`index.html`)
- Interface com 9 parceiros de laboratório
- Sistema modular (1 ativo + 8 em desenvolvimento)

### ✅ Comparador DB Diagnóstico (`comparador-db.html`)
- Upload e comparação de planilhas clínica × laboratório
- Busca interativa de pacientes
- Exportação formatada com 5 abas

---

## 📥 Como Usar

### 1. Acessar o Portal
```
Abra o arquivo index.html no navegador
```

### 2. Selecionar Parceiro
```
Clique no card verde "DB DIAGNÓSTICO"
```

### 3. Upload das Planilhas
```
• Planilha Clínica: exemplo-clinica.xlsx
• Planilha Laboratório: exemplo-laboratorio.xlsx
```

### 4. Processar Dados
```
Clique em "Processar ETL Completo"
Aguarde o processamento (5-10 segundos)
```

### 5. Baixar Resultado
```
Clique em "Baixar Planilha"
Excel formatado será baixado automaticamente
```

### 6. Buscar Pacientes (Opcional)
```
Use o campo de busca para análise individual
Copie tabelas específicas conforme necessário
```

---

## 📂 Estrutura do Projeto

```
clinica-meu-medico/
├── index.html               # Portal principal
├── financeiro.html          # Módulo Financeiro (conciliação bancária)
├── comparador-db.html       # Comparador DB Diagnóstico
├── parceiros.html           # Gestão de parceiros
├── MODULO-FINANCEIRO.md     # Documentação técnica do módulo financeiro
└── README.md
```

---

## 💡 Tecnologias Utilizadas

- **HTML5** - Estrutura semântica
- **CSS3** - Design responsivo com gradientes
- **JavaScript ES6+** - Lógica de processamento
- **ExcelJS** - Formatação avançada de planilhas
- **SheetJS** - Leitura de arquivos Excel

---

## 🎨 Paleta de Cores

```css
Verde Principal: #26a69a
Verde Escuro: #00796b
Verde Claro: #e8f5e9
Cinza: #f5f5f5
Azul: #2196F3
```

---

## 📊 Casos de Uso

### 1. Clínicas com Alto Volume
- Validação de centenas de exames em minutos
- Redução de 95% de erros manuais
- Economia de 10h/mês de trabalho

### 2. Laboratórios Parceiros
- Conferência de dados enviados
- Identificação de divergências
- Relatórios profissionais

### 3. Auditorias de Faturamento
- Comparação de registros
- Detecção de inconsistências
- Documentação completa

---

## 🔒 Segurança e Privacidade

✅ **100% Local** - Nenhum dado enviado para servidores
✅ **Processamento no Navegador** - Tudo acontece no seu computador
✅ **Sem Instalação** - Funciona direto no navegador
✅ **Dados Seguros** - Arquivos não são armazenados

---

## 🚀 Deploy no GitHub Pages

### Passo 1: Criar Repositório
```bash
git init
git add .
git commit -m "Initial commit - Portal Clínica Meu Médico"
```

### Passo 2: Conectar ao GitHub
```bash
git remote add origin https://github.com/seuusuario/clinica-meu-medico.git
git branch -M main
git push -u origin main
```

### Passo 3: Ativar GitHub Pages
```
1. Acesse Settings do repositório
2. Vá em Pages (menu lateral)
3. Source: Branch main
4. Clique em Save
5. Aguarde 2-3 minutos
```

### Passo 4: Acessar
```
https://seuusuario.github.io/clinica-meu-medico/
```

---

## 📧 Contato

**Desenvolvido por Mateus Monteiro**

📱 WhatsApp: (62) 99156-3421
📧 Email: [seu-email@exemplo.com]
💼 LinkedIn: [linkedin.com/in/seuperfil]

---

## 📝 Licença

Este projeto foi desenvolvido exclusivamente para **Clínica Meu Médico**.

---

## 🎯 Roadmap

**Módulo Financeiro**
- [x] Parsers Valori KS / MM / Santander com detecção automática
- [x] Parser ERP com lógica de DOC CORRIGIDO
- [x] Deduplicação por chave única
- [x] Plano de Contas com localStorage (add/edit/delete/restore)
- [x] Excel: aba LISTAS + aba APURAÇÃO + aba ERP
- [x] Fórmulas INDEX/MATCH, dropdown ALOCAÇÃO, formatação condicional
- [ ] Aba RESUMO (SUMIFS por categoria)
- [ ] Aba FLUXO DE CAIXA (por mês)
- [ ] Aba CONFERÊNCIA DE SALDOS
- [ ] Merge incremental (preservar ALOCAÇÃO preenchida)

**Portal de Parceiros**
- [x] Portal de Parceiros
- [x] Comparador DB Diagnóstico
- [ ] Neurocentro / Nova Era / AME Cardio / CEMED / São Lucas / CIMRAD / GT Diagnóstico / Center X

---

## 💬 Feedback

Encontrou algum problema ou tem sugestões?
Entre em contato: **(62) 99156-3421**

---

<div align="center">

**Desenvolvido com ❤️ para Clínica Meu Médico**

Sistema de Gestão v1.0 | Janeiro 2026

</div>
