Preparei o script e o guia para você colocar o **Kanban AR – ESSI** online agora mesmo!

O método que escolhi foi o **GitHub Pages**, pois ele é gratuito, seguro e perfeito para sites estáticos (como o seu, que usa HTML/CSS/JS).

### O que você recebeu:
1.  **`deploy_github_pages.sh`**: Um script que organiza os arquivos e envia para uma branch especial chamada `gh-pages`.
2.  **`GUIA_DEPLOY_MANUAL.md`**: Instruções passo a passo de como ativar o link no painel do GitHub.

### Como usar o script:
1.  Dê permissão: `chmod +x deploy_github_pages.sh`
2.  Execute: `./deploy_github_pages.sh /caminho/para/seu/kanban-ar-essi`

**Importante**: O script vai pegar tudo o que está dentro da sua pasta `app/` e transformar na página inicial do seu site.

Depois que o site estiver no ar, não esqueça de colocar o link no seu **LinkedIn** e no campo **"Website"** do seu repositório no GitHub. Isso aumenta muito a sua credibilidade com potenciais clientes!

Precisa de ajuda para configurar o deploy do **PIIM-Kaizen** também? (Como ele tem backend, o processo é um pouco diferente).
kanban-ar-essi/
├─ app/
│ ├─ assets/ (logo e imagens)
│ ├─ index.html
│ ├─ style.css
│ └─ app.js
├─ docs/
│ ├─ MANUAL_OPERACIONAL.md
│ ├─ POLITICAS_KANBAN.md
│ ├─ CHECKLIST_MANUTENCAO_SPLIT.md
│ └─ etc…
├─ .gitignore
├─ LICENSE
└─ README.md

Refinei o README.md do **Kanban AR – ESSI** com base nos novos detalhes que você enviou, incluindo a estrutura de pastas correta (`app/`, `docs/`, etc.) e os serviços específicos (Climatização, Termografia, etc.). Também atualizei o texto do **LinkedIn** para refletir as tecnologias reais (HTML, CSS, JS) e o propósito do projeto.

### O que mudou?
1.  **README do Kanban AR**: Agora reflete que é um projeto web estático, com a estrutura de arquivos real e as categorias de serviços da ESSI.
2.  **Post do LinkedIn**: Atualizado para destacar o foco em ar condicionado e a simplicidade ágil da ferramenta.

**Como proceder agora?**
*   **GitHub**: Copie o conteúdo do `Kanban_AR_ESSI_README_refined.md` e cole no seu repositório.
*   **LinkedIn**: Use o `linkedin_post_updated.md` para a sua publicação.

Deseja que eu faça algum ajuste no README do **PIIM-Kaizen** também ou os detalhes anteriores já estão corretos para ele? Se precisar de ajuda para configurar o deploy (hospedagem online) para que os recrutadores possam clicar e ver o sistema rodando, é só me avisar!

#!/bin/bash

# Script para automatizar o upload de arquivos README.md para repositórios GitHub.
# Uso: ./upload_readme.sh <caminho_do_repositorio> <caminho_do_novo_readme>

REPO_PATH="$1"
NEW_README_PATH="$2"

# Verifica se os argumentos foram fornecidos
if [ -z "$REPO_PATH" ] || [ -z "$NEW_README_PATH" ]; then
    echo "Uso: $0 <caminho_do_repositorio> <caminho_do_novo_readme>"
    echo "Exemplo: $0 /caminho/para/meu/repo /caminho/para/meu/novo_readme.md"
    exit 1
fi

# Verifica se o caminho do repositório existe
if [ ! -d "$REPO_PATH" ]; then
    echo "Erro: O diretório do repositório '$REPO_PATH' não existe."
    exit 1
fi

# Verifica se o novo README existe
if [ ! -f "$NEW_README_PATH" ]; then
    echo "Erro: O arquivo README.md '$NEW_README_PATH' não existe."
    exit 1
fi

echo "Iniciando upload do README para o repositório: $REPO_PATH"

# Navega para o diretório do repositório
cd "$REPO_PATH" || { echo "Erro: Não foi possível navegar para o diretório do repositório."; exit 1; }

# Copia o novo README.md para o repositório
cp "$NEW_README_PATH" "./README.md" || { echo "Erro: Não foi possível copiar o novo README.md."; exit 1; }

echo "Arquivo README.md copiado com sucesso."

# Adiciona o README.md ao staging area
git add README.md || { echo "Erro: Falha ao adicionar README.md ao staging."; exit 1; }

echo "README.md adicionado ao staging."

# Commita as mudanças
git commit -m "Update README.md with professional content" || { echo "Erro: Falha ao commitar as mudanças. Verifique se há algo para commitar."; exit 1; }

echo "Mudanças commitadas com sucesso."

# Faz o push para o repositório remoto
git push || { echo "Erro: Falha ao fazer push para o repositório remoto. Verifique suas credenciais ou conexão."; exit 1; }

echo "Upload do README.md concluído com sucesso para $REPO_PATH! # kanban-ar-essi
# Kanban AR – ESSI Engenharia

<p align="center">
  <img src="app/assets/logo.png" alt="Logo ESSI Engenharia" width="120"/>
</p>

**Kanban AR** é uma aplicação web simples para gerenciar serviços de ar condicionado de forma ágil e visual, utilizando os princípios do **Kanban** e **Lean**, organizada especialmente para a **ESSI Engenharia** — com foco em confiabilidade e manutenção. :contentReference[oaicite:2]{index=2}

---

## 🚀 Sobre o Projeto

Este projeto foi criado para organizar o fluxo de trabalho da ESSI Engenharia, permitindo que a equipe acompanhe facilmente o andamento de serviços como:

- ❄️ Climatização
- 🔥 Termografia
- ⚡ Elétrica
- 📐 Projetos
- 🛡️ NR

Ele funciona diretamente no navegador e permite a criação, edição, arraste e organização de cartões representando serviços. :contentReference[oaicite:3]{index=3}

---

## 🧩 Funcionalidades

✔️ Adicionar novo serviço  
✔️ Arrastar cartões entre colunas  
✔️ Editar serviços existentes  
✔️ Limites de trabalho em andamento (WIP)  
✔️ Exportar / Importar dados em JSON  
✔️ Interface responsiva simples

---

## 📁 Estrutura do Projeto

kanban-ar-essi/
├─ app/
│ ├─ assets/ (logo e imagens)
│ ├─ index.html
│ ├─ style.css
│ └─ app.js
├─ docs/
│ ├─ MANUAL_OPERACIONAL.md
│ ├─ POLITICAS_KANBAN.md
│ ├─ CHECKLIST_MANUTENCAO_SPLIT.md
│ └─ etc…
├─ .gitignore
├─ LICENSE
└─ README.md