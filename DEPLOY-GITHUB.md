# 🚀 GUIA COMPLETO - Deploy no GitHub Pages

Este guia vai te ensinar a colocar seu portal online **gratuitamente** usando GitHub Pages.

---

## ✅ PRÉ-REQUISITOS

1. **Conta no GitHub** (gratuita)
   - Acesse: https://github.com/signup
   - Crie sua conta se ainda não tiver

2. **Git instalado** (opcional, pode usar interface web)
   - Download: https://git-scm.com/downloads

---

## 📦 MÉTODO 1: UPLOAD DIRETO (Mais Fácil - SEM GIT)

### Passo 1: Criar Repositório

1. Acesse https://github.com
2. Clique no botão **"+"** no canto superior direito
3. Selecione **"New repository"**
4. Preencha:
   - **Repository name:** `clinica-meu-medico`
   - **Description:** `Portal de Automações - Clínica Meu Médico`
   - **Public** (para funcionar com GitHub Pages gratuito)
   - ✅ **Add a README file** (marque esta opção)
5. Clique em **"Create repository"**

### Passo 2: Upload dos Arquivos

1. No repositório criado, clique em **"Add file"** → **"Upload files"**
2. Arraste os seguintes arquivos:
   ```
   index.html
   comparador-db.html
   ```
3. Clique em **"Commit changes"**

### Passo 3: Upload da Pasta Exemplos

1. Clique novamente em **"Add file"** → **"Upload files"**
2. Arraste a pasta **exemplos** completa
3. Clique em **"Commit changes"**

### Passo 4: Ativar GitHub Pages

1. Vá em **Settings** (configurações do repositório)
2. No menu lateral, clique em **"Pages"**
3. Em **"Source"**, selecione:
   - Branch: **main**
   - Folder: **/ (root)**
4. Clique em **"Save"**
5. Aguarde **2-3 minutos**

### Passo 5: Acessar Seu Site

Seu site estará disponível em:
```
https://SEU-USUARIO.github.io/clinica-meu-medico/
```

**Exemplo:**
- Se seu usuário GitHub é `mateusmonteiro`
- URL será: `https://mateusmonteiro.github.io/clinica-meu-medico/`

---

## 💻 MÉTODO 2: USANDO GIT (Recomendado para Atualizações)

### Passo 1: Instalar Git

Windows:
```bash
https://git-scm.com/download/win
```

Mac:
```bash
brew install git
```

Linux:
```bash
sudo apt install git
```

### Passo 2: Configurar Git (Primeira Vez)

Abra o terminal/cmd e execute:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@example.com"
```

### Passo 3: Criar Repositório no GitHub

1. Acesse https://github.com/new
2. Nome: `clinica-meu-medico`
3. Public
4. **NÃO** marque "Add a README file"
5. Clique em "Create repository"

### Passo 4: Navegar até a Pasta DEPLOY

Abra o terminal/cmd:

```bash
cd "c:\Users\mateu\Desktop\CLINICA MEU MEDICO\DB EXAMES\DEPLOY"
```

### Passo 5: Inicializar Git

```bash
git init
git add .
git commit -m "Initial commit - Portal Clínica Meu Médico"
```

### Passo 6: Conectar ao GitHub

**Substitua `SEU-USUARIO` pelo seu usuário do GitHub:**

```bash
git remote add origin https://github.com/SEU-USUARIO/clinica-meu-medico.git
git branch -M main
git push -u origin main
```

**Quando pedir credenciais:**
- Usuário: seu usuário do GitHub
- Senha: **Personal Access Token** (não é a senha normal!)

#### Como gerar Personal Access Token:
1. GitHub → Settings → Developer settings
2. Personal access tokens → Tokens (classic)
3. Generate new token
4. Marque: `repo` (todas as opções)
5. Copie o token gerado (guarde bem!)

### Passo 7: Ativar GitHub Pages

1. Acesse o repositório no GitHub
2. Settings → Pages
3. Source: **Branch main**
4. Save
5. Aguarde 2-3 minutos

### Passo 8: Pronto!

Acesse: `https://SEU-USUARIO.github.io/clinica-meu-medico/`

---

## 🔄 ATUALIZANDO O SITE (Após Deploy Inicial)

### Quando você modificar algum arquivo:

```bash
cd "c:\Users\mateu\Desktop\CLINICA MEU MEDICO\DB EXAMES\DEPLOY"
git add .
git commit -m "Atualização: descreva o que mudou"
git push
```

Em **2-3 minutos** as mudanças estarão online!

---

## 🎨 PERSONALIZANDO O README NO GITHUB

Edite o arquivo `README.md` e substitua:

```markdown
👉 **[Acesse o Sistema](https://seuusuario.github.io/clinica-meu-medico/)**
```

Por:

```markdown
👉 **[Acesse o Sistema](https://SEU-USUARIO-REAL.github.io/clinica-meu-medico/)**
```

---

## 🐛 PROBLEMAS COMUNS

### 1. Erro 404 após Deploy
**Solução:** Aguarde 5 minutos e limpe o cache (Ctrl+Shift+R)

### 2. CSS não carrega
**Solução:** Verifique se todos os arquivos foram enviados

### 3. Planilhas não baixam
**Solução:** GitHub Pages tem limite de 100MB por arquivo

### 4. "Permission denied" ao fazer push
**Solução:** Use Personal Access Token ao invés da senha

### 5. Site não atualiza
**Solução:**
```bash
git push --force origin main
```
Aguarde 5 minutos

---

## 📧 PRECISA DE AJUDA?

**Mateus Monteiro**
WhatsApp: (62) 99156-3421

---

## ✅ CHECKLIST FINAL

- [ ] Conta no GitHub criada
- [ ] Repositório criado
- [ ] Arquivos enviados (index.html, comparador-db.html)
- [ ] Pasta exemplos enviada
- [ ] GitHub Pages ativado
- [ ] Aguardei 2-3 minutos
- [ ] Testei o link: `https://meuusuario.github.io/clinica-meu-medico/`
- [ ] Funcionou! 🎉

---

## 🎯 PRÓXIMOS PASSOS

1. ✅ Compartilhe o link com seu cliente
2. ✅ Adicione ao seu portfólio
3. ✅ Coloque no LinkedIn
4. ✅ Envie por WhatsApp

---

<div align="center">

**Seu portal está ONLINE! 🚀**

Compartilhe o link e impressione seus clientes!

</div>
