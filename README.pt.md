# Gemini Commit

Um script shell simples e poderoso para automatizar suas mensagens de commit no Git usando a CLI do Gemini do Google. Ele analisa suas alterações em *stage* e gera uma mensagem de commit descritiva seguindo o padrão *Conventional Commits*.

[Read in English](README.md)

---

## O Problema

Escrever mensagens de commit consistentes e de alta qualidade é uma tarefa crucial, mas muitas vezes tediosa. Ela exige aderência a padrões (como *Conventional Commits*), clareza e, por vezes, proficiência em inglês. Este script foi criado para resolver esse problema, delegando a tarefa para uma IA.

## Funcionalidades

-   **Mensagens via IA**: Usa o Google Gemini para gerar mensagens de commit com base no seu código em *stage* (`git diff --staged`).
-   **Conventional Commits**: Impõe o padrão *Conventional Commits* por padrão.
-   **Customização por Projeto**: Utiliza um arquivo `GEMINI.md` na raiz do seu projeto para fornecer instruções específicas à IA, tornando-o adaptável aos padrões de qualquer time.
-   **Integração com Área de Transferência**: Copia automaticamente a mensagem gerada para sua área de transferência (*clipboard*) para colar facilmente em sua IDE ou terminal.
-   **Foco em uma Mudança Específica**: Permite que você forneça um contexto extra para guiar o foco da IA.

## Pré-requisitos

Antes de começar, garanta que você tenha o seguinte instalado:
1.  **Git**: [https://git-scm.com/](https://git-scm.com/)
2.  **Gemini CLI**: Siga o guia de instalação oficial no [Google for Developers](https://blog.google/technology/developers/introducing-gemini-cli-open-source-ai-agent/). Certifique-se de que ela está autenticada e funcionando (`gemini -h`).

## Instalação

1.  **Clone o repositório (ou baixe os arquivos):**
    ```bash
    git clone https://github.com/vdurvalino/commit-assistant-gemini.git
    cd commit-assistant-gemini
    ```

2.  **Torne o script executável:**
    ```bash
    chmod +x commit
    ```

3.  **Mova o script para um diretório no PATH do seu sistema:**
    Uma escolha comum é `~/bin/` ou `/usr/local/bin`. Se você não tiver um, pode criá-lo.
    ```bash
    # Exemplo usando ~/bin
    mkdir -p ~/bin
    mv commit ~/bin/
    ```

4.  **Garanta que o diretório está no seu PATH:**
    Adicione a seguinte linha ao arquivo de configuração do seu shell (ex: `~/.zshrc`, `~/.bashrc`, ou `~/.bash_profile`), e então reinicie seu terminal ou execute `source ~/.zshrc`.
    ```bash
    export PATH="$HOME/bin:$PATH"
    ```

## Como Usar

Uma vez instalado, você pode executar o script de qualquer repositório git em sua máquina.

1.  **Adicione suas alterações ao stage:**
    ```bash
    git add <arquivo1> <arquivo2> ...
    ```

2.  **Gere a mensagem de commit:**
    ```bash
    commit
    ```
    O script exibirá a mensagem gerada e a copiará para sua área de transferência.

3.  **Gerar com contexto extra (foco):**
    Se quiser guiar a IA, passe o seu foco como um argumento.
    ```bash
    commit "refatorar o módulo de autenticação para usar o Strategy Pattern"
    ```

## Customização

Para adaptar as mensagens de commit às necessidades específicas do seu projeto, crie um arquivo `GEMINI.md` na raiz do seu repositório. A `gemini-cli` inclui automaticamente este arquivo no contexto de seus prompts.

Um modelo recomendado de `GEMINI.md` está incluído neste repositório. Você pode copiá-lo para o seu projeto e modificá-lo conforme necessário.

### Nota Crucial sobre Privacidade

A versão gratuita da Gemini CLI pode usar seus prompts (incluindo os diffs do seu código) para melhorar os serviços do Google. **Não use esta ferramenta em bases de código privadas ou proprietárias, a menos que você esteja usando um projeto Google Cloud configurado com garantias de privacidade de dados (ex: via Vertex AI).** Para ambientes profissionais, sempre utilize uma configuração corporativa.

## Licença

Este projeto está licenciado sob a Licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.