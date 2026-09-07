# 🐧 GuiaLinuxDebian

> Guia pessoal de comandos e configurações para **Ubuntu/Debian**.
>
> ⚠️ **Atenção:** alguns comandos são específicos do Ubuntu/GNOME ou podem variar conforme a versão da distribuição. Leia cada seção antes de executar comandos com `sudo`, remoção de pacotes ou alteração de configurações.

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

| Comando | Função |
|---|---|
| `chmod +x arquivo.sh` | Adiciona permissão de execução a um arquivo. |
| `chown usuario:usuario arquivo` | Altera o proprietário de um arquivo. |

## 1.6 🖥️ Terminal e sessão

| Comando / atalho | Função |
|---|---|
| `clear` | Limpa a tela do terminal. |
| `Ctrl + L` | Atalho para limpar a tela. |
| `exit` | Encerra a sessão do terminal. |
| `history` | Mostra o histórico de comandos digitados. |
| `man comando` | Mostra o manual de um comando. Ex.: `man ls`. |
| `source ~/.zshrc` | Recarrega as configurações do ZSH. |

## 1.7 📦 Gerenciamento de pacotes com APT

```bash
# Atualiza a lista de pacotes disponíveis
sudo apt update

# Atualiza os pacotes instalados
sudo apt upgrade -y

# Remove pacotes desnecessários
sudo apt autoremove -y

# Atualiza o sistema, remove dependências desnecessárias e limpa o cache
sudo apt update && sudo apt full-upgrade -y && sudo apt autoremove -y && sudo apt autoclean

# Instala um pacote
sudo apt install nome-do-pacote -y

# Remove um pacote instalado
sudo apt remove nome-do-pacote
```

### 🔄 Reiniciar e desligar

```bash
# Reinicia o computador
sudo reboot

# Desliga o computador imediatamente
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

# Verifica a configuração de áreas de trabalho dinâmicas
gsettings get org.gnome.mutter dynamic-workspaces

# Verifica a quantidade de áreas de trabalho
gsettings get org.gnome.desktop.wm.preferences num-workspaces
```

---

# 2. 📦 Instalação de aplicativos e ferramentas

## 2.1 🧰 Dependências básicas

Essas dependências são usadas para evitar problemas comuns com certificados, downloads, repositórios e pacotes.

```bash
sudo apt install -y \
curl \
wget \
git \
ca-certificates \
gnupg \
software-properties-common \
apt-transport-https
```

## 2.2 🌳 Tree

```bash
sudo apt install tree -y
```

## 2.3 🖥️ Ferramentas do sistema

```bash
# Personalização do GNOME
sudo apt install gnome-tweaks -y

# Integração de extensões do GNOME com navegador
sudo apt install chrome-gnome-shell -y

# Gerenciador de extensões do GNOME
sudo apt install gnome-shell-extension-manager -y

# Informações do sistema
sudo apt install neofetch -y
sudo apt install fastfetch -y

# Backup
sudo apt install timeshift -y

# Efeito inspirado no filme Matrix
sudo apt install cmatrix -y

# Visualização de áudio
sudo apt install cava -y

# Monitoramento do sistema
sudo apt install htop -y
sudo npm install gtop -g

# Gerenciador de discos
sudo apt install gparted -y
```

## 2.4 🟢 Node.js e npm

```bash
# Instala Node.js e npm pelos pacotes da distribuição
sudo apt install nodejs npm -y

# Verifica as versões instaladas
node -v
npm -v
```

## 2.5 🤖 Gemini CLI e Antigravity

```bash
# Configura o repositório do Node.js 22
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -

# Instala o Node.js
sudo apt install -y nodejs

# Instala o Gemini CLI
sudo npm install -g @google/gemini-cli

# Instala o Antigravity CLI
curl -fsSL https://antigravity.google/cli/install.sh | bash

# Adiciona os binários locais ao PATH do ZSH
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc

# Recarrega o ZSH
source ~/.zshrc

# Verifica as instalações
node -v
npm -v
gemini --version
agy --version
```

## 2.6 🧑‍💻 Visual Studio Code

### Opção recomendada: pacote `.deb` oficial

```bash
cd ~/Downloads

# Baixa a versão estável para Linux Debian/Ubuntu
wget -O code.deb \
"https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64"

# Instala o pacote
sudo apt install ./code.deb -y

# Verifica a instalação
code --version
```

### Alternativa: Snap

```bash
sudo snap install --classic code
```

## 2.7 🔀 Meld e Sublime Merge

```bash
# Meld
sudo apt install meld -y

# Sublime Merge
sudo snap install sublime-merge --classic
```

## 2.8 🐳 Docker e Docker Compose

> ⚠️ A seção abaixo segue o procedimento registrado no guia original para Ubuntu.

```bash
# Remove instalações antigas/conflitantes
sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc docker-buildx podman-docker containerd runc | cut -f1)

# Atualiza os pacotes
sudo apt update

# Instala dependências
sudo apt install ca-certificates curl

# Cria o diretório das chaves
sudo install -m 0755 -d /etc/apt/keyrings

# Adiciona a chave GPG oficial do Docker
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Adiciona o repositório do Docker
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF

# Atualiza a lista de pacotes
sudo apt update

# Instala Docker Engine, CLI, containerd, Buildx e Compose
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Verifica o Docker
docker --version

# Verifica o Docker Compose
docker compose version

# Permite executar Docker como usuário do grupo docker
sudo usermod -aG docker $USER
```

> Depois de adicionar o usuário ao grupo `docker`, pode ser necessário iniciar uma nova sessão para a alteração entrar em vigor.

## 2.9 💬 Discord

```bash
cd ~/Downloads

# Baixa o pacote .deb do Discord
wget 'https://discord.com/api/download?platform=linux&format=deb' -O discord.deb

# Confere o arquivo baixado
ls -lh discord.deb

# Instala o Discord
sudo apt install ./discord.deb

# Verifica o executável
which discord

# Verifica a versão
discord --version
```

## 2.10 ☕ Java / OpenJDK

```bash
# Atualiza a lista de pacotes
sudo apt update

# Instala o OpenJDK 25
sudo apt install -y openjdk-25-jdk

# Verifica o Java
java --version

# Verifica o compilador
javac --version

# Escolhe/verifica o Java padrão
update-alternatives --config java

# Escolhe/verifica o compilador padrão
update-alternatives --config javac

# Verifica os caminhos dos executáveis
which java
which javac

# Verifica o caminho real do Java
readlink -f "$(which java)"
```

## 2.11 🐍 Anaconda

```bash
# Atualiza o sistema
sudo apt update
sudo apt upgrade -y

# Instala dependências
sudo apt install -y curl wget bzip2 ca-certificates

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

# Remove a configuração do Conda adicionada ao Bash
~/anaconda3/bin/conda init --reverse bash

# Desativa o ambiente base da sessão atual
conda deactivate

# Verifica a instalação
conda --version
conda info --base

# Verifica o shell
echo $SHELL
ps -p $$ -o comm=
```

## 2.12 📦 Flatpak

```bash
# Instala o Flatpak
sudo apt install flatpak -y

# Integra o Flatpak ao GNOME Software
sudo apt install gnome-software-plugin-flatpak -y

# Adiciona o Flathub
sudo flatpak remote-add --if-not-exists flathub \
https://flathub.org/repo/flathub.flatpakrepo

# Reinicia o computador
sudo reboot

# Verifica os repositórios Flatpak
flatpak remotes
```

### Apps Flatpak

```bash
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

### Permissões para IDEs via Flatpak

```bash
# VS Code
flatpak override --user --filesystem=host com.visualstudio.code
flatpak override --user --device=all com.visualstudio.code

# Android Studio
flatpak override --user --filesystem=host com.google.AndroidStudio
flatpak override --user --device=all com.google.AndroidStudio

# IDEs JetBrains
flatpak override --user --filesystem=host com.jetbrains.IntelliJ-IDEA-Community
flatpak override --user --filesystem=host com.jetbrains.PyCharm-Community
flatpak override --user --filesystem=host com.jetbrains.CLion
flatpak override --user --filesystem=host com.jetbrains.PhpStorm

flatpak override --user --device=all com.jetbrains.IntelliJ-IDEA-Community
flatpak override --user --device=all com.jetbrains.PyCharm-Community
flatpak override --user --device=all com.jetbrains.CLion
flatpak override --user --device=all com.jetbrains.PhpStorm
```

### Comandos úteis do Flatpak

```bash
# Lista os aplicativos instalados
flatpak list

# Atualiza os aplicativos
flatpak update -y

# Remove um aplicativo
flatpak uninstall com.jetbrains.IntelliJ-IDEA-Community
```

## 2.13 🧰 JetBrains Toolbox

> O guia original recomenda o Toolbox para gerenciar IDEs JetBrains.

```bash
cd ~/Downloads

# Baixa o JetBrains Toolbox
wget https://download.jetbrains.com/toolbox/jetbrains-toolbox-2.8.0.51918.tar.gz

# Extrai
tar -xzf jetbrains-toolbox-*.tar.gz

# Entra na pasta extraída
cd jetbrains-toolbox-*/

# Executa o Toolbox
./jetbrains-toolbox
```

Pelo Toolbox, o guia recomenda instalar:

- IntelliJ IDEA Community
- PyCharm Community
- CLion
- PhpStorm

## 2.14 📱 Android Studio

> O guia original recomenda a instalação oficial para evitar problemas com SDK, Gradle, Emulator, ADB e virtualização.

```bash
cd ~/Downloads

# Baixa o Android Studio
wget -O android-studio.tar.gz \
https://redirector.gvt1.com/edgedl/android/studio/install/current/android-studio-*.tar.gz

# Cria a pasta de instalação
sudo mkdir -p /opt/android-studio

# Extrai para /opt
sudo tar -xzf android-studio.tar.gz \
-C /opt/android-studio \
--strip-components=1

# Cria um comando global
sudo ln -s /opt/android-studio/bin/studio /usr/local/bin/android-studio

# Abre o Android Studio
android-studio
```

Na primeira inicialização:

- Android SDK
- Android SDK Command-line Tools
- Android Emulator
- Android SDK Platform Tools

## 2.15 🎥 OBS Studio

```bash
# Atualiza a lista de pacotes
sudo apt update

# Instala o OBS Studio
sudo apt install obs-studio -y

# Verifica a instalação
obs --version
```

Para abrir:

```bash
obs
```

## 2.16 🛠️ GRUB Customizer

> ⚠️ O GRUB Customizer altera a configuração do bootloader. Use com cuidado e mantenha uma forma de recuperação do sistema caso alguma alteração impeça o sistema de iniciar.

```bash
# Atualiza a lista de pacotes
sudo apt update

# Instala o GRUB Customizer
sudo apt install grub-customizer -y
```

Para abrir:

```bash
grub-customizer
```

> 💡 Use o aplicativo principalmente para personalizar a ordem e a aparência das entradas do GRUB. Evite alterar configurações de boot sem saber exatamente o efeito da mudança.

## 2.17 🔧 Git + SSH + GitHub

### Criar/configurar uma chave SSH

```bash
# Verifica a pasta SSH
ls -la ~/.ssh

# Remove a chave antiga, caso necessário
rm -f ~/.ssh/id_ed25519 ~/.ssh/id_ed25519.pub

# Cria uma nova chave
# Substitua pelo e-mail associado ao GitHub
ssh-keygen -t ed25519 -C "SEU_EMAIL_REAL"

# Inicia o SSH Agent
eval "$(ssh-agent -s)"

# Adiciona a chave ao agente
ssh-add ~/.ssh/id_ed25519

# Verifica a chave adicionada
ssh-add -l

# Exibe a chave pública para copiar
cat ~/.ssh/id_ed25519.pub
```

No GitHub:

1. Acesse **Settings → SSH and GPG keys → New SSH key**.
2. Em **Title**, use um nome para identificar a máquina, por exemplo `Ubuntu`.
3. Em **Key type**, selecione `Authentication Key`.
4. Cole o conteúdo de `~/.ssh/id_ed25519.pub`.
5. Clique em **Add SSH key**.

### Testar a conexão

```bash
ssh -T git@github.com
```

Resultado esperado:

```text
Hi SEU_USUARIO! You've successfully authenticated,
but GitHub does not provide shell access.
```

### Configurar identidade do Git

```bash
git config --global user.name "Diogo Sales"
git config --global user.email "SEU_EMAIL_REAL"

# Verifica a configuração
git config --global --list
```

### Configurar um repositório para usar SSH

```bash
# Entre na pasta do repositório
cd CAMINHO/DO/SEU/REPOSITORIO

# Verifica o endereço remoto atual
git remote -v

# Troca HTTPS por SSH
# Substitua pela URL SSH do seu próprio repositório
git remote set-url origin git@github.com:USUARIO/REPOSITORIO.git

# Confere novamente
git remote -v
```

### Fluxo básico para enviar alterações

```bash
# Verifica o estado do repositório
git status

# Adiciona alterações
git add .

# Cria um commit
git commit -m "Atualiza projeto"

# Envia para o remoto
git push
```

---

# 3. 🐚 Instalação e configuração do ZSH

> Esta seção reúne as **duas versões de instalação do ZSH que estavam no arquivo original em uma única versão**, evitando repetição.
>
> O conjunto utilizado é: **ZSH + Oh My Zsh + Zinit + plugins + Starship + Nerd Font (opcional) + SDKMAN**.

## 3.1 Instalar ZSH

```bash
# Instala o ZSH
sudo apt-get install zsh -y

# Verifica a versão
zsh --version

# Define o ZSH como shell padrão
chsh -s $(which zsh)
```

> Após `chsh`, pode ser necessário sair da sessão e entrar novamente para iniciar o ZSH como shell padrão.

## 3.2 Instalar Curl e Git

```bash
# Instala o Curl
sudo apt-get install curl -y

# Verifica o Curl
curl --version

# Instala o Git
sudo apt-get install git -y

# Verifica o Git
git --version
```

## 3.3 Instalar Oh My Zsh

```bash
# Instala o Oh My Zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Abre a configuração do ZSH
nano ~/.zshrc

# Recarrega as configurações
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

> Como a configuração final abaixo utiliza o Zinit para carregar plugins, os clones acima ficam registrados aqui por serem parte do procedimento original. Não é necessário repetir a instalação em outra seção.

## 3.5 Instalar Zinit

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/zdharma-continuum/zinit/HEAD/scripts/install.sh)"
```

## 3.6 Instalar Starship

```bash
# Instala o Starship
curl -sS https://starship.rs/install.sh | sh

# Verifica a instalação
starship --version
```

## 3.7 Configurar o `~/.zshrc`

Abra o arquivo:

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

Salve com:

1. `Ctrl + O`
2. `Enter`
3. `Ctrl + X`

Depois recarregue:

```bash
source ~/.zshrc
```

## 3.8 🔤 Nerd Font — opcional

Esta etapa serve para melhorar a aparência do terminal, especialmente com temas, símbolos e ícones.

```bash
# Cria a pasta de fontes
mkdir -p ~/.local/share/fonts

# Entra na pasta
cd ~/.local/share/fonts

# Baixa a JetBrains Mono Nerd Font
wget https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.zip

# Extrai
unzip JetBrainsMono.zip

# Atualiza o cache de fontes
fc-cache -fv
```

Depois, nas configurações do terminal, selecione:

```text
JetBrainsMono Nerd Font
```

## 3.9 ⭐ Configurar o Starship

Crie a pasta de configuração:

```bash
mkdir -p ~/.config
```

Abra o arquivo:

```bash
nano ~/.config/starship.toml
```

Ou pelo VS Code:

```bash
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

Se preferir o tema azul triangular, substitua o conteúdo do `starship.toml` por:

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

## 📌 Observações finais

O guia original reúne ferramentas para uma máquina de desenvolvimento com foco em **Java, C/C++, Android, backend, Git e terminal personalizado**. A recomendação registrada no material é usar:

- **VS Code via `.deb`**
- **Android Studio oficial**
- **IDEs JetBrains via Toolbox**
- **Flatpak principalmente para aplicativos secundários**

A seção de ZSH foi consolidada para remover a duplicação existente no arquivo original. fileciteturn0file0L781-L908

---

> 💡 **Dica:** antes de executar uma sequência grande de comandos, faça a instalação por etapas e confirme cada etapa com os comandos de verificação disponíveis no próprio guia.
