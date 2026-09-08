# 🚀 Meu Hub de Guias de Configuração de Ambiente Linux

Este repositório é um hub centralizado de guias passo a passo para configuração de terminal, shell ZSH, ferramentas de desenvolvimento e personalização de ambiente no Linux.

Toda a instrução prévia de instalação e configuração foi refatorada, expandida e integrada diretamente dentro dos guias específicos para cada ecossistema de distribuição Linux.

---

## 📚 Guias Disponíveis

### 1. 🐧 [guiaLinuxDebian.md](./guiaLinuxDebian.md)
* **Público-Alvo:** Usuários de **Ubuntu, Debian e derivados** (ex: Linux Mint, Zorin OS, Pop!_OS).
* **Objetivo:** Guia completo de referência e configuração do sistema e terminal.
* **Resumo do Conteúdo:**
  * **Comandos Úteis de Terminal:** Comandos fundamentais de navegação, permissões (`chown`, `chmod`), gerenciamento de processos e atalhos.
  * **Gerenciamento de Pacotes (APT):** Atualização, instalação e manutenção de pacotes do sistema.
  * **Setup Completo do ZSH:** Passo a passo detalhado para instalação e configuração do ZSH, Oh My Zsh, gerenciador de plugins Zinit, preenchimento autocompletar, autosuggestions e sintaxe destacada.
  * **Personalização de Prompt e Estética:** Instalação e customização do **Starship Prompt** (`starship.toml`) e **Nerd Fonts** (JetBrains Mono).
  * **Ferramentas de Desenvolvimento:** Configurações adicionais de utilitários como SDKMAN, Node.js, Docker, Java, Git, Gemini CLI, Antigravity CLI e VS Code.

---

### 2. 🎩 [guiaLinuxFedora.md](./guiaLinuxFedora.md)
* **Público-Alvo:** Usuários de **Fedora Linux** e distribuições da família RHEL/RPM.
* **Objetivo:** Adaptar todos os passos do guia principal para o ecossistema Red Hat/Fedora.
* **Resumo do Conteúdo:**
  * **Gerenciamento de Pacotes (DNF):** Equivalentes exatos dos comandos APT utilizando o gerenciador de pacotes `dnf`.
  * **Setup do ZSH & Plugins:** Instalação do ZSH, Oh My ZSH, Zinit e plugins ajustados às particularidades do Fedora.
  * **Starship Prompt & Temas:** Configuração de prompt avançado, tratamento de fontes Nerd Fonts e repositórios específicos para Fedora.
  * **Resolução e Compatibilidade:** Instruções para instalação de pacotes e repositórios oficiais/externos no Fedora.

---

### 3. 🏹 [guiaLinuxArch.md](./guiaLinuxArch.md)
* **Público-Alvo:** Usuários de **Arch Linux** e distribuições derivadas (ex: EndeavourOS, Manjaro, Garuda Linux).
* **Objetivo:** Guia dedicado ao ecossistema *Rolling Release* do Arch Linux utilizando `pacman` e o helper AUR `yay`.
* **Resumo do Conteúdo:**
  * **Gerenciamento de Pacotes (Pacman & Yay):** Comandos essenciais do `pacman`, remoção de órfãos e compilação de pacotes via **AUR (Arch User Repository)**.
  * **Setup do ZSH & Plugins:** Instalação do ZSH, Oh My ZSH, Zinit e plugins otimizados para Arch Linux.
  * **Starship Prompt & Fontes:** Configuração de prompt, fontes `ttf-jetbrains-mono-nerd` e suporte estético completo no terminal.
  * **Ferramentas e IDEs:** Instalação de Docker, Java (`archlinux-java`), VS Code, Discord, JetBrains Toolbox, Android Studio, Anaconda e Flatpak.

---

## 🛠️ Como Utilizar Este Repositório

1. **Identifique sua distribuição:**
   * Se você usa Ubuntu, Debian, Linux Mint, Zorin OS ou Pop!_OS, consulte o [guiaLinuxDebian.md](./guiaLinuxDebian.md).
   * Se você usa Fedora ou RHEL, consulte o [guiaLinuxFedora.md](./guiaLinuxFedora.md).
   * Se você usa Arch Linux, EndeavourOS, Manjaro ou Garuda, consulte o [guiaLinuxArch.md](./guiaLinuxArch.md).

2. **Siga a ordem do guia escolhido:** Cada arquivo foi estruturado em sequência lógica para que você possa copiar, colar e executar os comandos do início ao fim sem quebrar dependências do sistema.

---
