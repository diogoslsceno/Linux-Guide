# 🐧 GuiaLinuxFedora

> Guia pessoal de comandos e configurações para **Fedora Linux**, distribuição mantida pelo projeto Fedora e patrocinada pela Red Hat.
>
> ⚠️ **Atenção:** este guia foi adaptado do `guiaLinuxDebian.md`. Comandos específicos de Debian/Ubuntu foram substituídos por equivalentes do Fedora quando há uma alternativa clara. Quando uma instalação depende de repositório externo ou não tem uma alternativa Fedora claramente suportada, isso é indicado no próprio guia.

---

# 1. 💻 Comandos úteis do terminal

## 1.1 📍 Navegação e diretórios

| Comando | Função |
|---|---|
| `pwd` | Mostra o caminho completo do diretório atual. |
| `ls` | Lista arquivos e pastas do diretório atual. |
| `cd nome-da-pasta` | Entra em uma pasta específica. |
| `cd ..` | Volta para o diretório anterior. |
| `cd ~` | Vai para o diretório home do usuário. |
| `mkdir nome-da-pasta` | Cria uma nova pasta. |
| `mkdir -p caminho/completo` | Cria múltiplas pastas caso não existam. |
| `touch arquivo.txt` | Cria um arquivo vazio. |
| `tree` | Mostra a estrutura de diretórios em formato de árvore. Requer instalação. |

## 1.2 📁 Copiar, mover e renomear

| Comando | Função |
|---|---|
| `mv antigo novo` | Renomeia arquivo ou pasta. |
| `mv arquivo destino/` | Move arquivo ou pasta para outro diretório. |
| `cp arquivo destino/` | Copia um arquivo para outro diretório. |
| `cp -r pasta destino/` | Copia uma pasta e todo o seu conteúdo. |

## 1.3 🗑️ Excluir arquivos e pastas

> ⚠️ Cuidado com `rm -rf`: a exclusão é forçada e pode apagar dados sem confirmação.

| Comando | Função |
|---|---|
| `rm arquivo.txt` | Remove um arquivo. |
| `rm -r pasta` | Remove uma pasta e seu conteúdo. |
| `rm -rf pasta` | Remove uma pasta e seu conteúdo forçando a exclusão. |
| `rmdir pasta` | Remove uma pasta vazia. |

## 1.4 📄 Visualização e edição

| Comando | Função |
|---|---|
| `cat arquivo.txt` | Exibe o conteúdo de um arquivo. |
| `nano arquivo.txt` | Abre um arquivo no editor Nano. |
| `code .` | Abre o diretório atual no Visual Studio Code. |
| `code arquivo.txt` | Abre um arquivo específico no Visual Studio Code. |

## 1.5 🔧 Permissões e proprietário

```bash
# Adiciona permissão de execução
chmod +x arquivo.sh

# Altera o proprietário de um arquivo
sudo chown usuario:usuario arquivo
```

## 1.6 🖥️ Terminal e sessão

| Comando / atalho | Função |
|---|---|
| `clear` | Limpa a tela do terminal. |
| `Ctrl + L` | Atalho para limpar a tela. |
| `exit` | Encerra a sessão do terminal. |
| `history` | Mostra o histórico de comandos digitados. |
| `man comando` | Mostra o manual de um comando. Ex.: `man ls`. |
| `source ~/.zshrc` | Recarrega as configurações do ZSH. |

## 1.7 📦 Gerenciamento de pacotes com DNF

No Fedora, o gerenciador de pacotes principal é o **DNF**.

```bash
# Atualiza o sistema
sudo dnf upgrade --refresh -y

# Instala um pacote
sudo dnf install nome-do-pacote -y

# Remove um pacote
sudo dnf remove nome-do-pacote -y

# Procura um pacote
dnf search nome-do-pacote

# Mostra informações de um pacote
dnf info nome-do-pacote

# Lista pacotes instalados
dnf list installed

# Remove dependências que não são mais necessárias
sudo dnf autoremove -y

# Limpa caches
sudo dnf clean all
```

### 🔄 Reiniciar e desligar

```bash
# Reinicia
sudo reboot

# Desliga imediatamente
sudo shutdown now
```

### 🖥️ Configurações do GNOME

```bash
# Define a opacidade do perfil padrão do Ptyxis para 55%
gsettings set org.gnome.Ptyxis.Profile:/org/gnome/Ptyxis/Profiles/$(gsettings get org.gnome.Ptyxis default-profile-uuid | tr -d \')/ opacity 0.55

# Desativa áreas de trabalho dinâmicas
gsettings set org.gnome.mutter dynamic-workspaces false

# Define 5 áreas de trabalho
gsettings set org.gnome.desktop.wm.preferences num-workspaces 5

# Verifica a configuração
gsettings get org.gnome.mutter dynamic-workspaces
gsettings get org.gnome.desktop.wm.preferences num-workspaces
```

---

# 2. 📦 Instalação de aplicativos e ferramentas

## 2.1 🧰 Dependências básicas

```bash
# Atualiza o sistema
sudo dnf upgrade --refresh -y

# Ferramentas comuns para downloads, chaves, compilação e Git
sudo dnf install -y \
curl \
wget \
git \
ca-certificates \
gnupg2 \
tar \
unzip \
gcc \
gcc-c++ \
make \
python3
```

## 2.2 🌳 Tree

```bash
sudo dnf install tree -y
```

## 2.3 🖥️ Ferramentas do sistema

```bash
# Personalização do GNOME
sudo dnf install gnome-tweaks -y

# Gerenciador de extensões do GNOME
sudo dnf install gnome-extensions-app -y

# Informações do sistema
sudo dnf install fastfetch -y

# Backup
sudo dnf install timeshift -y

# Efeito inspirado no filme Matrix
sudo dnf install cmatrix -y

# Visualização de áudio
sudo dnf install cava -y

# Monitoramento do sistema
sudo dnf install htop -y

# Gerenciador de discos
sudo dnf install gparted -y
```

> `neofetch` não é necessário no Fedora moderno se você já utiliza `fastfetch`.

## 2.4 🟢 Node.js e npm

```bash
# Instala Node.js e npm
sudo dnf install nodejs npm -y

# Verifica as versões
node -v
npm -v
```

### Node.js 22 e ferramentas como Gemini CLI

```bash
# Verifica os pacotes disponíveis
dnf info nodejs

# Depois de garantir uma versão compatível, instale os pacotes
sudo dnf install nodejs npm -y

# Instala o Gemini CLI
sudo npm install -g @google/gemini-cli

# Verifica
node -v
npm -v
gemini --version
```

> O procedimento original utilizava o repositório NodeSource para Ubuntu. No Fedora, prefira primeiro os pacotes e mecanismos de versão disponibilizados pelo próprio Fedora. Se uma ferramenta exigir especificamente Node 22, confira a versão disponível na sua edição do Fedora antes de adicionar um repositório externo.

## 2.5 🤖 Antigravity CLI

```bash
# Instala o Antigravity CLI
curl -fsSL https://antigravity.google/cli/install.sh | bash

# Adiciona os binários locais ao PATH do ZSH
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc

# Recarrega o ZSH
source ~/.zshrc

# Verifica
agy --version
```

## 2.6 🧑‍💻 Visual Studio Code

### Instalação pelo repositório RPM da Microsoft

```bash
# Importa a chave da Microsoft
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Adiciona o repositório oficial
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\nautorefresh=1\nrepo_gpgcheck=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'

# Atualiza os metadados
sudo dnf check-update

# Instala o VS Code
sudo dnf install code -y

# Verifica
code --version
```

## 2.7 🔀 Meld e Sublime Merge

```bash
# Meld
sudo dnf install meld -y
```

> Para o Sublime Merge, prefira o pacote RPM/repositório oficial da Sublime. Como a URL e o método podem mudar, não é recomendado fixar um endereço antigo neste guia.

## 2.8 🐳 Docker Engine e Docker Compose

> O Fedora utiliza RPM/DNF. O procedimento abaixo usa o repositório oficial do Docker. A documentação atual do Docker recomenda o repositório RPM para o Docker Engine. citeturn0search1

```bash
# Remove versões conflitantes, caso existam
sudo dnf remove docker \
docker-client \
docker-client-latest \
docker-common \
docker-latest \
docker-latest-logrotate \
docker-logrotate \
docker-selinux \
docker-engine-selinux \
docker-engine

# Adiciona o repositório oficial do Docker
sudo dnf config-manager addrepo --from-repofile https://download.docker.com/linux/fedora/docker-ce.repo

# Instala Docker Engine, CLI, containerd, Buildx e Compose
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

# Inicia o Docker e configura para iniciar com o sistema
sudo systemctl enable --now docker

# Verifica
docker --version
docker compose version

# Testa o Docker
sudo docker run hello-world

# Permite executar Docker sem sudo
sudo usermod -aG docker $USER
```

> Depois de adicionar seu usuário ao grupo `docker`, encerre a sessão e entre novamente para que a alteração de grupo seja aplicada.

## 2.9 💬 Discord

> No Fedora, uma opção simples é utilizar o Flatpak.

```bash
# Instala o Discord pelo Flathub
flatpak install flathub com.discordapp.Discord -y

# Executa
flatpak run com.discordapp.Discord
```

## 2.10 ☕ Java / OpenJDK

```bash
# Lista versões disponíveis
dnf search openjdk

# Exemplo: instala o OpenJDK disponível no repositório
sudo dnf install java-latest-openjdk-devel -y

# Verifica o Java
java --version

# Verifica o compilador
javac --version

# Verifica os caminhos
which java
which javac

# Mostra o caminho real do Java
readlink -f "$(which java)"
```

> Se você precisar de uma versão específica do JDK, como 17, 21 ou 25, consulte primeiro `dnf search openjdk` e instale o pacote correspondente à versão disponível no seu Fedora.

## 2.11 🐍 Anaconda

```bash
# Atualiza o sistema
sudo dnf upgrade --refresh -y

# Instala dependências
sudo dnf install -y curl wget bzip2 ca-certificates

# Vai para Downloads
cd ~/Downloads

# Baixa o instalador
wget https://repo.anaconda.com/archive/Anaconda3-2026.07-1-Linux-x86_64.sh

# Executa o instalador
bash Anaconda3-2026.07-1-Linux-x86_64.sh

# Inicializa o Conda para ZSH
~/anaconda3/bin/conda init zsh

# Aplica as alterações
source ~/.zshrc

# Não ativa o ambiente base automaticamente
conda config --set auto_activate_base false

# Remove a configuração adicionada ao Bash
~/anaconda3/bin/conda init --reverse bash

# Desativa o ambiente base da sessão atual
conda deactivate

# Verifica
conda --version
conda info --base

# Verifica o shell
echo $SHELL
ps -p $$ -o comm=
```

## 2.12 📦 Flatpak

O Fedora Workstation já possui integração com Flatpak, mas o Flathub pode ser habilitado para ampliar o catálogo.

```bash
# Instala Flatpak caso ainda não esteja instalado
sudo dnf install flatpak -y

# Adiciona o Flathub
flatpak remote-add --if-not-exists flathub \
https://flathub.org/repo/flathub.flatpakrepo

# Verifica os repositórios
flatpak remotes
```

### Apps Flatpak

```bash
# Discord
flatpak install flathub com.discordapp.Discord -y

# OBS Studio
flatpak install flathub com.obsproject.Studio -y

# IntelliJ IDEA Community
flatpak install flathub com.jetbrains.IntelliJ-IDEA-Community -y

# PyCharm Community
flatpak install flathub com.jetbrains.PyCharm-Community -y

# CLion
flatpak install flathub com.jetbrains.CLion -y

# PhpStorm
flatpak install flathub com.jetbrains.PhpStorm -y

# Android Studio
flatpak install flathub com.google.AndroidStudio -y

# Visual Studio Code
flatpak install flathub com.visualstudio.code -y
```

### Comandos úteis do Flatpak

```bash
# Lista aplicativos instalados
flatpak list

# Atualiza aplicativos
flatpak update -y

# Remove um aplicativo
flatpak uninstall com.jetbrains.IntelliJ-IDEA-Community
```

## 2.13 🎥 OBS Studio

> Para distribuições Linux que não sejam Ubuntu, o próprio projeto OBS recomenda o **Flathub** como método de instalação. citeturn0search5turn0search6

```bash
# Instala o OBS Studio pelo Flathub
flatpak install flathub com.obsproject.Studio -y

# Abre o OBS
flatpak run com.obsproject.Studio
```

## 2.14 🛠️ GRUB Customizer

> ⚠️ O GRUB Customizer altera a configuração do bootloader. No Fedora, ele **não deve ser tratado como um pacote padrão equivalente ao `apt install grub-customizer` do Ubuntu**. A disponibilidade depende de repositórios de terceiros e da versão do Fedora.
>
> Por segurança, este guia não fixa um repositório de terceiros sem verificar a compatibilidade com a versão instalada.

### Verificar se está disponível nos repositórios habilitados

```bash
dnf search grub-customizer
```

Se o pacote aparecer em um repositório confiável e compatível com sua versão:

```bash
sudo dnf install grub-customizer -y
```

Depois:

```bash
grub-customizer
```

> 💡 Antes de modificar o GRUB, mantenha um método de recuperação do Fedora disponível. Evite alterar parâmetros de boot sem saber exatamente o efeito.

## 2.15 🧰 JetBrains Toolbox

```bash
cd ~/Downloads

# Baixa o JetBrains Toolbox
wget https://download.jetbrains.com/toolbox/jetbrains-toolbox-2.8.0.51918.tar.gz

# Extrai
tar -xzf jetbrains-toolbox-*.tar.gz

# Entra na pasta
cd jetbrains-toolbox-*/

# Executa
./jetbrains-toolbox
```

Pelo Toolbox, você pode instalar:

- IntelliJ IDEA Community
- PyCharm Community
- CLion
- PhpStorm

## 2.16 📱 Android Studio

### Opção Flatpak

```bash
flatpak install flathub com.google.AndroidStudio -y
```

Para executar:

```bash
flatpak run com.google.AndroidStudio
```

Na primeira inicialização:

- Android SDK
- Android SDK Command-line Tools
- Android Emulator
- Android SDK Platform Tools

> A instalação oficial do Android Studio também pode ser usada. O importante é manter SDK, Gradle, ADB e Emulator consistentes com a forma de instalação escolhida.

## 2.17 🔧 Git + SSH + GitHub

### Verificar a pasta SSH

```bash
ls -la ~/.ssh
```

### Criar uma nova chave

```bash
# Remove uma chave antiga, caso seja realmente necessário
rm -f ~/.ssh/id_ed25519 ~/.ssh/id_ed25519.pub

# Cria uma nova chave
ssh-keygen -t ed25519 -C "SEU_EMAIL_REAL"
```

Quando aparecer o caminho para salvar a chave, pressione `Enter` para aceitar o padrão.

### Iniciar o SSH Agent

```bash
eval "$(ssh-agent -s)"

# Adiciona a chave
ssh-add ~/.ssh/id_ed25519

# Verifica
ssh-add -l
```

### Exibir a chave pública

```bash
cat ~/.ssh/id_ed25519.pub
```

No GitHub:

1. **Settings → SSH and GPG keys → New SSH key**
2. Escolha um título para identificar o computador.
3. Selecione `Authentication Key`.
4. Cole o conteúdo de `~/.ssh/id_ed25519.pub`.
5. Clique em **Add SSH key**.

### Testar

```bash
ssh -T git@github.com
```

Resultado esperado:

```text
Hi SEU_USUARIO! You've successfully authenticated,
but GitHub does not provide shell access.
```

### Configurar nome e e-mail

```bash
git config --global user.name "Diogo Sales"
git config --global user.email "SEU_EMAIL_REAL"

# Verifica
git config --global --list
```

### Configurar o remoto SSH

```bash
# Entra no repositório
cd CAMINHO/DO/SEU/REPOSITORIO

# Verifica o remoto
git remote -v

# Troca HTTPS por SSH
git remote set-url origin git@github.com:USUARIO/REPOSITORIO.git

# Confere
git remote -v
```

### Fluxo básico

```bash
# Verifica alterações
git status

# Adiciona arquivos
git add .

# Cria commit
git commit -m "Atualiza projeto"

# Envia para o GitHub
git push
```

---

# 3. 🐚 Instalação e configuração do ZSH

> Esta seção consolida a configuração do guia original em uma única versão para Fedora.
>
> Conjunto utilizado: **ZSH + Oh My Zsh + Zinit + plugins + Starship + Nerd Font (opcional) + SDKMAN**.

## 3.1 Instalar ZSH

```bash
# Instala o ZSH
sudo dnf install zsh -y

# Verifica
zsh --version

# Define o ZSH como shell padrão
chsh -s $(which zsh)
```

> Depois do `chsh`, pode ser necessário sair da sessão e entrar novamente.

## 3.2 Instalar Curl e Git

```bash
sudo dnf install curl git -y

curl --version
git --version
```

## 3.3 Instalar Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Abra a configuração:

```bash
nano ~/.zshrc
```

Depois:

```bash
source ~/.zshrc
```

## 3.4 Instalar plugins

```bash
# Syntax highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# Sugestões automáticas
git clone https://github.com/zsh-users/zsh-autosuggestions \
${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

## 3.5 Instalar Zinit

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/zdharma-continuum/zinit/HEAD/scripts/install.sh)"
```

## 3.6 Instalar Starship

```bash
curl -sS https://starship.rs/install.sh | sh

starship --version
```

## 3.7 Configurar o `~/.zshrc`

```bash
nano ~/.zshrc
```

Adicione ao final:

```zsh
### Plugins via Zinit

zinit light zdharma-continuum/fast-syntax-highlighting
zinit light zsh-users/zsh-autosuggestions
zinit light zsh-users/zsh-completions
zinit light zsh-users/zsh-history-substring-search
zinit light hlissner/zsh-autopair
zinit light Aloxaf/fzf-tab
zinit light agkozak/zsh-z
zinit light zdharma-continuum/history-search-multi-word

### Starship Prompt

eval "$(starship init zsh)"

### SDKMAN

export SDKMAN_DIR="$HOME/.sdkman"
[[ -s "$HOME/.sdkman/bin/sdkman-init.sh" ]] && source "$HOME/.sdkman/bin/sdkman-init.sh"
```

Salve:

1. `Ctrl + O`
2. `Enter`
3. `Ctrl + X`

Recarregue:

```bash
source ~/.zshrc
```

## 3.8 🔤 Nerd Font — opcional

```bash
# Cria a pasta de fontes
mkdir -p ~/.local/share/fonts

# Entra na pasta
cd ~/.local/share/fonts

# Baixa a JetBrains Mono Nerd Font
wget https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.zip

# Extrai
unzip JetBrainsMono.zip

# Atualiza o cache
fc-cache -fv
```

Depois, nas configurações do terminal, selecione:

```text
JetBrainsMono Nerd Font
```

## 3.9 ⭐ Configurar o Starship

```bash
mkdir -p ~/.config

# Pelo Nano
nano ~/.config/starship.toml

# Ou pelo VS Code
code ~/.config/starship.toml
```

### Tema original

```toml
format = """
[░▒▓](#a3aed2)\
[  ](bg:#a3aed2 fg:#090c0c)\
[](bg:#769ff0 fg:#a3aed2)\
$directory\
[](fg:#769ff0 bg:#394260)\
$git_branch\
$git_status\
[](fg:#394260 bg:#212736)\
$nodejs\
$rust\
$golang\
$php\
[](fg:#212736 bg:#1d2230)\
$time\
[ ](fg:#1d2230)\
\n$character"""

[directory]
style = "fg:#e3e5e5 bg:#769ff0"
format = "[ $path ]($style)"
truncation_length = 3
truncation_symbol = "…/"

[directory.substitutions]
"Documents" = "󰈙 "
"Downloads" = " "
"Music" = " "
"Pictures" = " "

[git_branch]
symbol = ""
style = "bg:#394260"
format = '[[ $symbol $branch ](fg:#769ff0 bg:#394260)]($style)'

[git_status]
style = "bg:#394260"
format = '[[($all_status$ahead_behind )](fg:#769ff0 bg:#394260)]($style)'

[nodejs]
symbol = ""
style = "bg:#212736"
format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'

[rust]
symbol = ""
style = "bg:#212736"
format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'

[golang]
symbol = ""
style = "bg:#212736"
format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'

[php]
symbol = ""
style = "bg:#212736"
format = '[[ $symbol ($version) ](fg:#769ff0 bg:#212736)]($style)'

[time]
disabled = false
time_format = "%R"
style = "bg:#1d2230"
format = '[[  $time ](fg:#a0a9cb bg:#1d2230)]($style)'
```

### Tema azul alternativo

```toml
format = """
[░▒▓](#021644)\
[   ](bg:#021644 fg:#E6ECFF)\
[](bg:#0A2A66 fg:#021644)\
$directory\
[](fg:#0A2A66 bg:#0F2F73)\
$git_branch\
$git_status\
[](fg:#0F2F73 bg:#081D4A)\
$rust\
$golang\
$php\
[](fg:#081D4A bg:#061738)\
$time\
[ ](fg:#061738)\
\n$character"""

[directory]
style = "fg:#E6ECFF bg:#0A2A66"
format = "[ $path ]($style)"
truncation_length = 3
truncation_symbol = "…/"

[directory.substitutions]
"Documents" = "󰈙 "
"Downloads" = " "
"Music" = " "
"Pictures" = " "

[git_branch]
symbol = ""
style = "bg:#0F2F73"
format = '[[ $symbol $branch ](fg:#8FB3FF bg:#0F2F73)]($style)'

[git_status]
style = "bg:#0F2F73"
format = '[[($all_status$ahead_behind )](fg:#8FB3FF bg:#0F2F73)]($style)'

[nodejs]
symbol = ""
style = "bg:#081D4A"
format = '[[ $symbol ($version) ](fg:#8FB3FF bg:#081D4A)]($style)'

[rust]
symbol = ""
style = "bg:#081D4A"
format = '[[ $symbol ($version) ](fg:#8FB3FF bg:#081D4A)]($style)'

[golang]
symbol = ""
style = "bg:#081D4A"
format = '[[ $symbol ($version) ](fg:#8FB3FF bg:#081D4A)]($style)'

[php]
symbol = ""
style = "bg:#081D4A"
format = '[[ $symbol ($version) ](fg:#8FB3FF bg:#081D4A)]($style)'

[time]
disabled = false
time_format = "%R"
style = "bg:#061738"
format = '[[  $time ](fg:#C6D4FF bg:#061738)]($style)'
```

---

# 📌 Observações finais

A principal diferença entre este guia e o guia Debian/Ubuntu é o gerenciamento de pacotes:

| Debian / Ubuntu | Fedora |
|---|---|
| `apt` | `dnf` |
| `.deb` | `.rpm` |
| `dpkg` | `rpm` |
| PPA | Repositórios RPM / COPR / repositórios oficiais |
| Snap / Flatpak | Flatpak é uma opção especialmente útil para apps desktop |

Para uma máquina de desenvolvimento Fedora, uma combinação prática é:

- **DNF** para pacotes do sistema
- **Flatpak + Flathub** para aplicativos desktop
- **VS Code via RPM**
- **Android Studio via Flatpak ou instalação oficial**
- **JetBrains Toolbox** para IDEs JetBrains
- **Docker Engine pelo repositório oficial**
- **ZSH + Oh My Zsh + Zinit + Starship** para o terminal
- **Git + SSH** para GitHub

> 💡 **Importante:** Fedora é baseado no ecossistema RPM e possui diferenças importantes em relação ao Debian/Ubuntu. Não copie comandos `apt`, `add-apt-repository`, PPAs ou caminhos de `.deb` deste guia Debian para o Fedora.
