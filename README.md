# Debian WSL, ZSH and Cmder

This is a guide on getting Debian WSL, ZSH and Cmder working together without bugs.

## Install

- Go to the Windows Store and install Debian WSL
- Run the following:

  ```bash
  sudo apt update
  sudo apt upgrade
  sudo apt install zsh git curl
  ```

## Install Oh-My-Zsh and configure Cmder

- Run the following to install Oh-My-Zsh:

  ```bash
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
  ```

- Change your default shell to zsh:

  ```bash
  chsh -s $(which zsh)
  ```

- Create a new task in Cmder with the following placed in **Commands**:

  ```
  %ConEmuBaseDirShort%\wsl\wslbridge.exe
  ```

This works in Windows versions past 1703. After this verison, Windows made WSL look at your default shell and run it if no arguments are run with it. Additionally, you need to use `wslbridge.exe` in order to integrate WSL with WinAPI. Otherwise, you will get bugs such as the arrow keys not working in Vim.

If you want the Debian icon, you will have to manually download it. Cmder only supports `.ico`, and the Debian WSL icon comes with PNG icons.

Please use the following as a reference:

[ConEmu: WSL](https://conemu.github.io/en/BashOnWindows.html)
