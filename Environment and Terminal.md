## VS Code
  - Text Editor with built-in terminal
  - Open Terminal shortcut: `Ctrl + ~`
  - You can open VS Code using the `code` command from the terminal
  - Extensions:
    - Markdown All in One
    - WSL
  - [Linux Shortcuts](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-linux.pdf)
  - [Windows Shortcuts](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)
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
  - Oh My ZSH - a framework for working with ZSH (installing plugins, configuration, etc.)
  - `zsh` - restart terminal
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

- Add to ~/.zshrc:
  - `sudo hwclock -s` (forces WSL clock to stay in-sync with system clock)

## PyEnv/Python
See current version: `python3 --version`

### Install [pyenv](https://github.com/pyenv/pyenv):
  - `curl https://pyenv.run | bash`
  - Terminal output: Add these lines to `~/.zshrc`:
```shell
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
```

### Install python versions using pyenv:
  - Check installed versions: `pyenv versions`
  - See all versions available for install: `pyenv install --list`
  - Install a selected version: `pyenv install <version>`
    - Possible error: ```shell configure: error: no acceptable C compiler found in $PATH```
    - Resolution: [PyEnv Wiki](https://github.com/pyenv/pyenv/wiki#suggested-build-environment) - replace `apt` with `apt-get`:
```shell
sudo apt-get update
sudo apt-get install \
    build-essential libssl-dev zlib1g-dev \
    libbz2-dev libreadline-dev libsqlite3-dev curl git \
    libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev \
    libffi-dev liblzma-dev
```
### Switch between versions using pyenv:
  - Check installed versions: `pyenv versions`
  - Set Python version for current terminal: `pyenv shell <version>`
  - Set Python version globally: `pyenv global <version>`

### Virtual Environments

- Each project should have it's own virtual environment
- Only install packages to virutal enviornments, not the system python.
- 
```sh
# create a virtual environment 
# in a folder called "./venv/"
python -m venv ./venv/
  
# activate the virtual environment 
# so that "pip install ..." lands 
# packages into "./venv/lib/site-packages/" 
# and python programs executed with
# "python ./path/to/some/script.py" 
# evaluates "import" statements using 
# the packages in the 
# "./venv/lib/site-packages/" folder
source ./venv/bin/activate   # or ". ./venv/bin/activate"
  
# deactivate the virtual environment 
# to stop the behaviors caused 
# by activating a venv
deactivate
```




## AWS CLI
  - Google the installation instructions
  - Check version of AWS CLI: `aws --version` 
    - Should have at least major version 2
  - Validate your credentials: `aws sts get-caller-identity`
  - Configure credentials: `aws configure`
      - AWS Access Key ID / AWS Secret Access Key
        - Create Access Key Pair: IAM > Users > user > Create access key > Command Line Interface (CLI)
      - Default region name: us-west-2
      - Potential error: `An error occurred (SignatureDoesNotMatch) when calling the GetCallerIdentity operation: Signature expired: 20230822T072529Z is now earlier than 20230822T193257Z (20230822T194757Z - 15 min.)`
        - Resolution: Check date using `date`. If the date is incorrect, run `sudo hwclock -s`
    - Configs/credentials are stored in `~/.aws`
      - Additional *profiles* can be added here
        - Don't let your *default* profile have admin access
        - Configure new profile programatically: `aws configure --profile <profile-name>`
