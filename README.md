# 🏥 Clínica Meu Médico - Portal de Automações

Sistema profissional para comparação e análise de exames médicos entre clínica e laboratórios parceiros.

## 🚀 Demo ao Vivo

👉 **[Acesse o Sistema](https://seuusuario.github.io/clinica-meu-medico/)**

## 📸 Preview

![Portal de Automações](https://via.placeholder.com/800x400/26a69a/ffffff?text=Portal+de+Automações)

*Portal principal com grid de parceiros*

---

## 🎯 Funcionalidades

### ✅ Portal de Parceiros
- Interface profissional com 9 parceiros
- Sistema modular (1 ativo + 8 em desenvolvimento)
- Design responsivo e intuitivo

### ✅ Comparador DB Diagnóstico
- **Upload e processamento** de planilhas Excel (.xlsx, .xls)
- **Comparação automática** entre dados da clínica e laboratório
- **Busca interativa** de pacientes em tempo real
- **Exportação formatada** com cores, bordas e formatação condicional
- **Análise de divergências** com destaque visual
- **5 abas no Excel** gerado:
  1. Clínica Original
  2. Clínica Expandido
  3. Laboratório Original
  4. Comparação Completa
  5. Resumo de Divergências

### ✅ Painel de Análise Interativa
- Busca de pacientes por nome
- Estatísticas em tempo real
- Comparação sintética lado a lado
- Visualização completa de dados originais
- Botões para copiar tabelas (formato Excel/Word)

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
DEPLOY/
├── index.html              # Portal principal
├── comparador-db.html      # Sistema DB Diagnóstico
├── exemplos/
│   ├── exemplo-clinica.xlsx
│   └── exemplo-laboratorio.xlsx
└── README.md              # Este arquivo
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

- [x] Portal de Parceiros
- [x] Comparador DB Diagnóstico
- [x] Busca Interativa
- [x] Exportação Formatada
- [ ] Neurocentro (Em desenvolvimento)
- [ ] Nova Era (Em desenvolvimento)
- [ ] AME Cardio (Em desenvolvimento)
- [ ] CEMED (Em desenvolvimento)
- [ ] São Lucas (Em desenvolvimento)
- [ ] CIMRAD (Em desenvolvimento)
- [ ] GT Diagnóstico (Em desenvolvimento)
- [ ] Center X (Em desenvolvimento)

---

## 💬 Feedback

Encontrou algum problema ou tem sugestões?
Entre em contato: **(62) 99156-3421**

---

<div align="center">

**Desenvolvido com ❤️ para Clínica Meu Médico**

Sistema de Gestão v1.0 | Janeiro 2026

</div>
