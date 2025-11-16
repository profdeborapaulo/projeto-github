#  Estrutura da Automação

O projeto utiliza **dois workflows separados**, seguindo o padrão profissional de DevOps.

---

## 1. CI — Integração Contínua (`ci.yml`)

Arquivo em:  
`.github/workflows/ci.yml`

###  O que ele faz?

- Baixa o código do repositório  
- Instala Node.js  
- Valida automaticamente:
  - HTML (html5validator)
  - CSS (Stylelint)
  - JavaScript (ESLint)

###  Objetivo

Garantir a **qualidade do código** antes do deploy.

---

## 2. CD — Deploy Contínuo (`deploy.yml`)

Arquivo em:  
`.github/workflows/deploy.yml`

###  Quando ele roda?

- Sempre que há **push na branch main**

###  O que ele faz?

- Baixa o código  
- Prepara o ambiente do GitHub Pages  
- Envia os arquivos estáticos como artefato  
- Publica automaticamente  

---

#  Como Desenvolver no Projeto

## 1. Clone o repositório

```bash
git clone <url-do-repositorio>
cd nome-do-projeto
```

## 2. Instale dependências (opcional)

```bash
npm install
```

## 3. Trabalhe normalmente

Edite os arquivos HTML, CSS e JS normalmente.

## 4. Commit e push

```bash
git add .
git commit -m "Minha atualização"
git push
```

---

#  Style Guide do Projeto

##  HTML
- Usar identação de 2 espaços  
- Usar tags semânticas  
- Fechar todas as tags  

##  CSS
- Seletores simples  
- Evitar IDs  
- Usar classes padronizadas  

##  JavaScript
- camelCase  
- Funções pequenas  
- const e let  

---

#  Validação Local

```bash
npx stylelint "**/*.css"
npx eslint "**/*.js"
```

---

#  Runbook

## 1. CI falhou por HTML  
Abra o log para ver a linha do erro.

## 2. Stylelint erro  
Indentação, espaçamento ou seletor inválido.

## 3. ESLint erro  
Variável não usada, falta ponto e vírgula, função não declarada.

## 4. Deploy não atualiza  
Verificar execução do workflow e branch do Pages.
