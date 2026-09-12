# 🚀 Hub de Guias de Configuração de Ambiente Linux

Este repositório é um hub centralizado de guias passo a passo para configuração de terminal, shell ZSH, ferramentas de desenvolvimento e personalização de ambiente no Linux.

Toda a instrução de instalação e configuração foi refatorada, expandida e integrada em guias dedicados para cada distribuição na pasta [`guias/`](./guias/).

---

## 📁 Estrutura do Repositório

```text
guia-linux/
└── guias/
    ├── arch.md
    ├── debian.md
    └── fedora.md
├── .gitignore
├── README.md
```

---

## 📚 Guias Disponíveis

### 1. 🐧 [Debian & Ubuntu (`guias/debian.md`)](./guias/debian.md)
* **Público-Alvo:** Usuários de **Ubuntu, Debian e derivados** (ex: Linux Mint, Zorin OS, Pop!_OS).
* **Objetivo:** Guia completo de referência e configuração do sistema e terminal.
* **Resumo do Conteúdo:**
  * **Comandos Úteis de Terminal:** Navegação, permissões (`chown`, `chmod`), gerenciamento de processos e atalhos.
  * **Gerenciamento de Pacotes (APT):** Atualização, instalação e manutenção de pacotes do sistema.
  * **Setup do ZSH & Plugins:** ZSH, Oh My Zsh, Zinit, autosuggestions e sintaxe destacada.
  * **Prompt & Estética:** **Starship Prompt** e **Nerd Fonts** (JetBrains Mono).
  * **Ferramentas de Dev:** SDKMAN, Node.js, Docker, Java, Git, Gemini CLI, Antigravity CLI e VS Code.
  * **Customização do GRUB:** Instalação do Tema Vimix, backup, remoção de submenus/recovery e otimização de boot.

---

### 2. 🎩 [Fedora Linux (`guias/fedora.md`)](./guias/fedora.md)
* **Público-Alvo:** Usuários de **Fedora Linux** e distribuições da família RHEL/RPM.
* **Objetivo:** Adaptar todos os passos do guia principal para o ecossistema Red Hat/Fedora.
* **Resumo do Conteúdo:**
  * **Gerenciamento de Pacotes (DNF):** Equivalentes dos comandos APT utilizando o `dnf`.
  * **Setup do ZSH & Plugins:** ZSH, Oh My Zsh e Zinit ajustados para Fedora.
  * **Prompt & Estética:** Configuração avançada de prompt e fontes no Fedora.
  * **Ferramentas e Compatibilidade:** Docker Engine, RPM oficial do VS Code, Flatpak/Flathub e ferramentas de dev.
  * **Customização do GRUB:** Instalação do Tema Vimix, backup e otimização do bootloader no Fedora.

---

### 3. 🏹 [Arch Linux (`guias/arch.md`)](./guias/arch.md)
* **Público-Alvo:** Usuários de **Arch Linux** e derivados (ex: EndeavourOS, Manjaro, Garuda Linux).
* **Objetivo:** Guia dedicado ao ecossistema *Rolling Release* utilizando `pacman` e o helper AUR `yay`.
* **Resumo do Conteúdo:**
  * **Gerenciamento de Pacotes (Pacman & Yay):** Comandos essenciais do `pacman`, gerenciamento de órfãos e AUR.
  * **Setup do ZSH & Plugins:** ZSH, Oh My Zsh e Zinit otimizados para Arch.
  * **Prompt & Fontes:** Prompt Starship e pacotes de fontes `ttf-jetbrains-mono-nerd`.
  * **Ferramentas e IDEs:** Docker, Java (`archlinux-java`), VS Code, Discord, JetBrains Toolbox, Android Studio e Flatpak.
  * **Customização do GRUB:** Instalação do Tema Vimix, backup e limpeza de menus no Arch Linux.

---

## 🛠️ Como Utilizar Este Repositório

1. **Identifique sua distribuição:**
   * Se você usa Ubuntu, Debian, Linux Mint, Zorin OS ou Pop!_OS, consulte o [guias/debian.md](./guias/debian.md).
   * Se você usa Fedora ou RHEL, consulte o [guias/fedora.md](./guias/fedora.md).
   * Se você usa Arch Linux, EndeavourOS, Manjaro ou Garuda, consulte o [guias/arch.md](./guias/arch.md).

2. **Siga a ordem do guia escolhido:** Cada arquivo foi estruturado em sequência lógica para que você possa copiar, colar e executar os comandos do início ao fim sem quebrar dependências do sistema.

---
