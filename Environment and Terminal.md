## VS Code
  ## Environment and Terminal Setup

  This readme provides instructions for setting up the environment and terminal for a Python software engineering project.

  ### Text Editor with Built-in Terminal

  To streamline your workflow, it is recommended to use a text editor with a built-in terminal. One popular option is Visual Studio Code (VS Code). You can open the terminal in VS Code using the shortcut `Ctrl + ~`.

  ### Opening VS Code from the Terminal

  To open VS Code directly from the terminal, you can use the `code` command. Simply navigate to the desired project folder in the terminal using the `cd` command, and then run `code .` to open the folder in VS Code as a workspace.

  ### Extensions

  There are several useful extensions for VS Code that can enhance your coding experience. Two recommended extensions for working with Markdown files are "Markdown All in One" and "WSL" (Windows Subsystem for Linux).

  ### Shortcuts

  For quick reference, you can find a list of keyboard shortcuts for VS Code on Linux and Windows in the following links:

  - [Linux Shortcuts](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-linux.pdf)
  - [Windows Shortcuts](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)

  ## Ubuntu (or other Linux OS)

  If you are using Ubuntu or another Linux operating system, follow these steps to set up your environment and terminal:

  ### Install WSL on Windows

  If you are using Windows 10 or later, you can install Windows Subsystem for Linux (WSL) to run a Linux environment. Here's how:

  1. Open PowerShell as Administrator.
  2. Run the command `wsl --list --online` to see the available Linux distributions.
  3. Run the command `wsl --install -d <Distro>` to install the desired Linux distribution. Replace `<Distro>` with the name of the distribution you want to install.
  4. Set up a username and password for the Linux distribution.
    - Note: The `sudo` command will require your password.
  5. Integrate WSL with VS Code:
    - Install the "WSL" VS Code Extension.
    - Open the Ubuntu terminal.
    - Navigate to your project folder using the `cd` command.
    - Run `code .` to open the folder in VS Code as a workspace.

  ## Git

  To update Git to the latest version, follow these steps:

  1. Check the current version of Git by running `git --version`.
  2. Run the following commands to update Git:
    - `sudo add-apt-repository ppa:git-core/ppa`
    - `sudo apt-get update`
    - `sudo apt-get install git`

  ## Oh My ZSH

  Oh My ZSH is a framework for working with ZSH (Z-Shell), which is a "superset" of bash. Use the following commands to install Oh My ZSH and its plugins:
  ```shell
  # Update apt-get to install the most up-to-date versions of packages
  apt-get update

  # Install sed, git, and zsh if they aren't already present
  which sed || sudo apt-get install -y sed || echo "linux: could not install sed"
  which zsh || sudo apt-get install -y zsh || echo "linux: could not install zsh"
  which git \
     || sudo add-apt-repository ppa:git-core/ppa \
     && sudo apt-get update \
     && sudo apt-get install -y git \
     || echo "mac: could not install git"

  # Install OhMyZSH if it isn't already installed
  [ -d ~/.oh-my-zsh ] || sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

  # Install the zsh-autosuggestions plugin
  git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

  # Install the zsh-syntax-highlighting plugin
  git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

  # Enable the zsh-autosuggestions and zsh-syntax-highlighting plugins
  sed -i 's/\(^plugins=([^)]*\)/\1 python pip pyenv virtualenv web-search zsh-autosuggestions zsh-syntax-highlighting/' "$HOME/.zshrc"

  # Set the ZSH_THEME to "bira"
  sed -i 's/_THEME=\".*\"/_THEME=\"bira\"/g' "$HOME/.zshrc"
  ```
  You can restart the terminal by running `zsh`.
   
  ### Additional Configuration

  Add the following line to your `~/.zshrc` file to synchronize the WSL clock with the system clock:

  ```shell
  sudo hwclock -s
  ```

  ## PyEnv/Python

  To manage multiple Python versions, you can use pyenv. Here's how to install and use pyenv:

  ### Install pyenv

  To install pyenv, run the following command:

  ```shell
  curl https://pyenv.run | bash
  ```

  After installation, add the following lines to your `~/.zshrc` file:

  ```shell
  export PYENV_ROOT="$HOME/.pyenv"
  export PATH="$PYENV_ROOT/bin:$PATH"
  eval "$(pyenv init --path)"
  ```

  ### Install Python Versions

  To install specific Python versions using pyenv, follow these steps:

  1. Check the installed versions by running `pyenv versions`.
  2. To see all available versions for installation, run `pyenv install --list`.
  3. Install a selected version by running `pyenv install <version>`.
     - If you encounter the error `configure: error: no acceptable C compiler found in $PATH`, refer to the [PyEnv Wiki](https://github.com/pyenv/pyenv/wiki#suggested-build-environment) for the resolution (replace `apt` with `apt-get`).

  ### Switch Between Versions

  To switch between installed Python versions using pyenv, use the following commands:

  - Check the installed versions: `pyenv versions`.
  - Set the Python version for the current terminal: `pyenv shell <version>`.
  - Set the Python version globally: `pyenv global <version>`.

  ### Virtual Environments

  It is recommended to create a virtual environment for each project to isolate dependencies. Follow these steps to create and activate a virtual environment:

  ```shell
  # Create a virtual environment in a folder called "./venv/"
  python -m venv ./venv/

  # Activate the virtual environment
  source ./venv/bin/activate   # or ". ./venv/bin/activate"

  # Deactivate the virtual environment
  deactivate
  ```

  ## AWS CLI

  To work with the AWS Command Line Interface (CLI), follow these steps:

  - Google the installation instructions for AWS CLI.
  - Check the version of AWS CLI by running `aws --version`. Make sure you have at least version 2.
  - Validate your credentials by running `aws sts get-caller-identity`.
  - Configure your credentials by running `aws configure`. Provide your AWS Access Key ID, AWS Secret Access Key, and default region name.
    - To create an Access Key Pair, go to IAM > Users > user > Create access key > Command Line Interface (CLI).
  - The AWS CLI configurations and credentials are stored in `~/.aws`. You can add additional profiles for different AWS accounts by editing the configuration file.
    - Avoid giving admin access to the *default* profile.
    - To configure a new profile programmatically, run `aws configure --profile <profile-name>`.

