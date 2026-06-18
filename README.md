# Instalação do ZSH + Oh My ZSH + Zinit + Starship em Sistemas Baseados em Debian

## 1. Instalar o ZSH

```bash
sudo apt update
sudo apt-get install zsh -y
```

### Verifique a instalação

```bash
zsh --version
```

### Defina o ZSH como shell padrão

```bash
chsh -s $(which zsh)
```

---

## 2. Instalar o Curl

```bash
sudo apt-get install curl -y
```

### Verifique a instalação

```bash
curl --version
```

---

## 3. Instalar o Git

```bash
sudo apt update
sudo apt-get install git -y
```

### Verifique a instalação

```bash
git --version
```

---

## 4. Instalar o Oh My ZSH

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Abra o arquivo de configuração do ZSH

```bash
nano ~/.zshrc
```

### Recarregue as configurações

```bash
source ~/.zshrc
```

---

## 5. Instalar Plugins do Oh My ZSH

### zsh-syntax-highlighting

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

### zsh-autosuggestions

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

---

## 6. Instalar o Zinit

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/zdharma-continuum/zinit/HEAD/scripts/install.sh)"
```

---

## 7. Instalar o Starship Prompt

```bash
curl -sS https://starship.rs/install.sh | sh
```

### Verifique a instalação

```bash
starship --version
```

---

## 8. Configurar o ZSH

Abra novamente o arquivo:

```bash
nano ~/.zshrc
```

Cole o conteúdo abaixo ao final do arquivo:

```bash
### Fim do trecho de instalação do Zinit

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

### Salvar o arquivo

1. Pressione `Ctrl + O`
2. Pressione `Enter`
3. Pressione `Ctrl + X`

### Recarregue as configurações

```bash
source ~/.zshrc
```

---

# Instalar Nerd Fonts (Opcional)

Esta etapa é opcional e serve para melhorar a aparência do terminal, especialmente ao utilizar temas e ícones.

## 1. Baixar e instalar a fonte

```bash
sudo apt update

sudo apt-get install wget unzip -y

mkdir -p ~/.local/share/fonts
cd ~/.local/share/fonts

wget https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.zip

unzip JetBrainsMono.zip

fc-cache -fv
```

## 2. Selecionar a fonte no terminal

Abra as configurações do terminal e selecione:

```text
JetBrainsMono Nerd Font
```

## 3. Criar a configuração do Starship

Crie a pasta de configuração caso ela não exista:

```bash
mkdir -p ~/.config
```

Abra o arquivo:

```bash
nano ~/.config/starship.toml
```

ou

```bash
code ~/.config/starship.toml
```

## 4. Configurar o tema do Starship

Cole o tema original abaixo ou utilize sua versão personalizada:

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

[rust]
symbol = ""
style = "bg:#081D4A"
format = '[[ $symbol ](fg:#8FB3FF bg:#081D4A)]($style)'

[golang]
symbol = ""
style = "bg:#081D4A"
format = '[[ $symbol ](fg:#8FB3FF bg:#081D4A)]($style)'

[php]
symbol = ""
style = "bg:#081D4A"
format = '[[ $symbol ](fg:#8FB3FF bg:#081D4A)]($style)'

[time]
disabled = false
time_format = "%R"
style = "bg:#061738"
format = '[[  $time ](fg:#C6D4FF bg:#061738)]($style)'
```
