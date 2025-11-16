# Pipeline CI/CD para Site Estático (GitHub Actions + GitHub Pages)

Este repositório demonstra como configurar **CI (Integração Contínua)** e **CD (Entrega Contínua)** usando GitHub Actions para projetos front-end simples (HTML, CSS e JavaScript).

O objetivo é ensinar boas práticas de automação, validação de código e publicação automática de sites.

---

# Estrutura da Automação

O projeto utiliza **dois workflows separados**, seguindo o padrão profissional de DevOps:

---

## 1. CI — Integração Contínua (`ci.yml`)

Arquivo em:
.github/workflows/ci.yml


### O que ele faz?

- Baixa o código do repositório  
- Instala Node.js  
- Valida automaticamente:
  - HTML (html5validator)
  - CSS (Stylelint)
  - JavaScript (ESLint)

### Objetivo

Garantir a **qualidade do código** antes do deploy.  
Se houver erros, o GitHub marca o PR/push como **falhou**.

---

## 2. CD — Deploy Contínuo para GitHub Pages (`deploy.yml`)

Arquivo em:
.github/workflows/deploy.yml


### Quando ele roda?

- Sempre que houver **push na branch `main`**

### O que ele faz?

- Baixa o código  
- Prepara o ambiente do GitHub Pages  
- Envia os arquivos estáticos como artefato  
- Publica automaticamente no seu site GitHub Pages

### Onde o site fica disponível?
https://profdeborapaulo.github.io/projeto-github/

---

# Como Desenvolver no Projeto

## 1. Clone o repositório

```bash
git clone <url-do-repositório>
cd nome-do-projeto

2. Instale dependências (opcional)
npm install
Se não existir package.json, o CI vai tratar isso automaticamente.

3. Trabalhe normalmente no seu código

modifique arquivos HTML, CSS, JS

4. Faça commit e push
git add .
git commit -m "Minha atualização"
git push

---
## O que acontece após o push?

CI valida

Se passar → CI 

Se falhar → CI (deploy não é bloqueado, mas recomendado corrigir)

CD publica o site automaticamente


## Style Guide do Projeto

Para manter consistência, siga estas regras:

1. HTML

a. Usar identação de 2 espaços
b. Preferir tags semânticas (header, section, article, footer)
c. Fechar todas as tags

2. CSS

a. Seletores simples e claros
b. Nada de IDs para estilizar
c. Classes devem ser padronizadas

.btn-primary
.card-title
.header-nav
3. JavaScript

a. Funções curtas e reutilizáveis
b. Nome de variáveis em camelCase
c. Evitar variáveis globais
d. Usar sempre const e let (nunca var)

## Validação Local

Para testar antes de fazer push:
npx stylelint "**/*.css"
npx eslint "**/*.js"

## Runbook — Como Resolver Problemas Comuns
1. O CI falhou por erro de HTML
 -- Abra o log → ele mostra a linha do erro.

2. Stylelint acusou erro
Normalmente é:

-- identação incorreta
-- espaçamento faltando
-- seletor inválido

3. ESLint acusou erro
Pode ser:

a. variável não usada
b. falta de ponto e vírgula
c. função não declarada

4.  Deploy não atualizou o site
Verifique:

a. o workflow deploy.yml foi executado?
b. houve erro em "Upload Pages artifact"?
c. branch usada no Pages é a correta (github-pages automático do GitHub)?
