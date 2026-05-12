# Plano de Contas — Como adicionar ou editar itens

O Plano de Contas é definido diretamente no código-fonte do arquivo `financeiro.html`.
Abra o arquivo em qualquer editor de texto (VS Code, Notepad++, etc.) e localize o array `DEFAULT_CATS`.

## Onde fica no código

Busque pelo texto `DEFAULT_CATS` no arquivo — você encontrará um bloco assim:

```js
const DEFAULT_CATS = [
  // DESPESAS ADMINISTRATIVAS
  {ref:'1.1',  custo:'FIXO',    disc:'AGUA E ESGOTO',         cat:'DESPESAS ADMINISTRATIVAS'},
  ...
];
```

## Como adicionar um novo item

Copie qualquer linha existente como modelo e ajuste os 4 campos:

```js
{ref:'1.17', custo:'FIXO', disc:'NOME DA CONTA', cat:'DESPESAS ADMINISTRATIVAS'},
```

| Campo  | O que é | Exemplos |
|--------|---------|---------|
| `ref`  | Código de referência (deve ser único) | `1.17`, `4.11`, `9.8` |
| `custo`| Tipo de custo | `FIXO` ou `VARIAVEL` |
| `disc` | Discriminação (nome da conta — em maiúsculas) | `ALUGUEL`, `FOLHA DE PAGAMENTO` |
| `cat`  | Categoria pai | ver lista abaixo |

## Categorias disponíveis

```
DESPESAS ADMINISTRATIVAS
DESPESAS COM PESSOAL
DESPESAS FINANCEIRAS
DIVIDENDOS
FINANCEIRO
SALDO ANTERIOR
```

Para criar uma nova categoria, basta usar um nome diferente no campo `cat`.

## Como editar um item existente

Localize a linha pelo campo `disc` e altere o valor desejado diretamente.

## Como remover um item

Delete a linha inteira (incluindo a vírgula no final, se houver).

## Exemplo completo

```js
// DESPESAS ADMINISTRATIVAS
{ref:'1.1',  custo:'FIXO',    disc:'AGUA E ESGOTO',                      cat:'DESPESAS ADMINISTRATIVAS'},
{ref:'1.2',  custo:'FIXO',    disc:'ALUGUEL',                            cat:'DESPESAS ADMINISTRATIVAS'},
// novo item adicionado:
{ref:'1.17', custo:'VARIAVEL',disc:'ESTACIONAMENTO',                     cat:'DESPESAS ADMINISTRATIVAS'},
```

## Importante

Após salvar o arquivo, faça o deploy (push para o GitHub) para que a alteração apareça online.
A chave de alocação gerada automaticamente segue o padrão:

```
REF - CUSTO - DISCRIMINAÇÃO - CATEGORIA
Exemplo: 1.17 - VARIAVEL - ESTACIONAMENTO - DESPESAS ADMINISTRATIVAS
```

Essa chave é usada nas colunas de ALOCAÇÃO da planilha Excel gerada.
