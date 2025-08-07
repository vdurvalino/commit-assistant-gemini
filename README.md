# Gemini Commit

A simple and powerful shell script to automate your Git commit messages using Google's Gemini CLI. It analyzes your staged changes and generates a descriptive commit message following the Conventional Commits standard.

[Leia em Português](README.pt.md)

---

## The Problem

Writing consistent, high-quality commit messages is a crucial but often tedious task. It demands adherence to standards (like Conventional Commits), clarity, and sometimes, proficiency in English. This script was created to solve that problem by delegating the task to an AI.

## Features

-   **AI-Powered Messages**: Uses Google's Gemini to generate commit messages based on your staged code (`git diff --staged`).
-   **Conventional Commits**: Enforces the Conventional Commits standard by default.
-   **Project-Specific Customization**: Uses a `GEMINI.md` file in your project's root to provide specific instructions to the AI, making it adaptable to any team's standards.
-   **Clipboard Integration**: Automatically copies the generated message to your clipboard for easy pasting into your IDE or terminal.
-   **Focus on a Specific Change**: Allows you to provide extra context to guide the AI's focus.

## Prerequisites

Before you begin, ensure you have the following installed:
1.  **Git**: [https://git-scm.com/](https://git-scm.com/)
2.  **Gemini CLI**: Follow the official installation guide at [Google for Developers](https://blog.google/technology/developers/introducing-gemini-cli-open-source-ai-agent/). Make sure it's authenticated and working (`gemini -h`).

## Installation

1.  **Clone the repository (or download the files):**
    ```bash
    git clone https://github.com/vdurvalino/commit-assistant-gemini.git
    cd commit-assistant-gemini
    ```

2.  **Make the script executable:**
    ```bash
    chmod +x commit
    ```

3.  **Move the script to a directory in your system's PATH:**
    A common choice is `~/bin/` or `/usr/local/bin`. If you don't have one, you can create it.
    ```bash
    # Example using ~/bin
    mkdir -p ~/bin
    mv commit ~/bin/
    ```

4.  **Ensure the directory is in your PATH:**
    Add the following line to your shell's configuration file (e.g., `~/.zshrc`, `~/.bashrc`, or `~/.bash_profile`), then restart your terminal or run `source ~/.zshrc`.
    ```bash
    export PATH="$HOME/bin:$PATH"
    ```

## Usage

Once installed, you can run the script from any git repository on your machine.

1.  **Stage your changes:**
    ```bash
    git add <file1> <file2> ...
    ```

2.  **Generate the commit message:**
    ```bash
    commit
    ```
    The script will output the generated message and copy it to your clipboard.

3.  **Generate with extra context (focus):**
    If you want to guide the AI, pass your focus as an argument.
    ```bash
    commit "refactor the auth module to use the Strategy Pattern"
    ```

## Customization

To tailor the commit messages to your project's specific needs, create a `GEMINI.md` file in the root of your repository. The `gemini-cli` automatically includes this file in the context of its prompts.

A recommended `GEMINI.md` template is included in this repository. You can copy it to your project and modify it as needed.

### Crucial Note on Privacy

The free version of the Gemini CLI may use your prompts (including your code diffs) to improve Google's services. **Do not use this tool on private or proprietary codebases unless you are using a configured Google Cloud project with data privacy guarantees (e.g., via Vertex AI).** For professional environments, always use an enterprise-grade setup.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.