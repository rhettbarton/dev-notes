## VS Code
  - Text Editor with built-in terminal
  - Open Terminal shortcut: `Ctrl + ~`
  - You can open VS Code using the `code` command from the terminal
  
## Ubuntu (or other Linux OS)
  - Install WSL on Windows (Windows 10 or later):
    - Powershell > Run as Administrator > `wsl --list --online` > `wsl --install -d <Distro>`
    - Set up username and password
      - `sudo` requires password
    - Integrate with VS Code:
      - Install `WSL` VS Code Extension
      - Open Ubuntu terminal
        - `cd` into project folder
        - `code .` > *opens the folder in VS Code as a workspace*
  
## Git
  - Update To Latest Version:
    - `git --version`
    - `sudo add-apt-repository ppa:git-core/ppa` 
    - `sudo apt-get update`
    - `sudo apt-get install git`

## Oh My ZSH
  - ZSH (Z-Shell) is a "superset" of bash
  - Oh My ZSH - a framework for working with ZSH (intalling plugins, configuration, etc.)
  - Cheatsheet:
````shell
# update apt-get so it will install the most up-to-date versions of packages
apt-get update

# try to install sed, git, and zsh if they aren't already present
# Note: sed is a command for editing text files, we will use it further down
# to configure the ~/.zshrc file
which sed || sudo apt-get install -y sed || echo "linux: could not install sed"
which zsh || sudo apt-get install -y zsh || echo "linux: could not install zsh"
which git \
    || sudo add-apt-repository ppa:git-core/ppa \
    && sudo apt-get update \
    && sudo apt-get install -y git \
    || echo "mac: could not install git"

# install OhMyZSH if it isn't already installed
[ -d ~/.oh-my-zsh ] || sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# plugin: zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# plugin: zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# add these two plugins and enable some of the default ones
sed -i 's/\(^plugins=([^)]*\)/\1 python pip pyenv virtualenv web-search zsh-autosuggestions zsh-syntax-highlighting/' "$HOME/.zshrc"

# set the ZSH_THEME to "bira"
sed -i 's/_THEME=\".*\"/_THEME=\"bira\"/g' "$HOME/.zshrc"

````