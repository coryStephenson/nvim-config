# nvim-config

This is my very first attempt at a basic Lua config file for Neovim. In addition to the features therein, I noticed that I was not able to invoke Neovim beyond one session. This URL contained the solution that resolved my problem on my Kubuntu machine: [How to create a permanent Bash alias on Linux/Unix - nixCraft](https://www.cyberciti.biz/faq/create-permanent-bash-alias-linux-unix/).

As seen below, `/opt/nvim-linux-x86_64/bin/nvim` is the absolute path that was returned when I issued the `whereis nvim` command.

```console
1521  touch ~/.bash_aliases
1522  ls
1523  whereis nvim
1524  /opt/nvim-linux-x86_64/bin/nvim ~/.bashrc
1525  /opt/nvim-linux-x86_64/bin/nvim ~/.bash_aliases
1526  source ~/.bash_aliases
1527  nvim
```
## Contents of ~/.bash_aliases

```console
alias nvim='/opt/nvim-linux-x86_64/bin/nvim'
```
## Copying and Pasting to and from Neovim

Source: [How can I copy and paste outside of Neovim?](https://askubuntu.com/questions/1486871/how-can-i-copy-and-paste-outside-of-neovim)



In order to be able to paste text copied from Neovim to any app, you have to copy the text to the system clipboard. You can do that as follows:

    
    Install a clipboard tool, because, as indicated in your screenshot, you don't have one installed.

        Indicate which type of graphics server session you're on by:

        echo $XDG_SESSION_TYPE
        
        If you are on an Xorg session, you may install either xsel or xclip by running:

        sudo apt install xsel

        or:

        sudo apt install xclip

        If you are on a Wayland session, you may install wl-clipboard by running:

        sudo apt install wl-clipboard

    Select the text you wish to copy in Neovim.

    Press the following keys one at a time: "+y

    This copies (y) the selected text to the selection register ("+).

    Paste the selected text to the app you wish to using the usual paste shortcut Ctrl+V.

To make things easier, you can also have the text you copy in Neovim always copied to the system clipboard by adding the following in your ~/.config/nvim/init.vim file (create the file if it doesn't exist or go to the correct file location if you use a custom Neovim setup):

set clipboard=unnamedplus

If you are using the Lua API for configuring Neovim, you can achieve the same using the command in kkvamshee's answer.

## Building Neovim from source

Source: [Build Neovim from source](https://neovim.io/doc2/build/)

```console
1 mkdir Git-Repos
2 cd Git_Repos/
3 sudo apt update
4 sudo apt-get install ninja-build gettext cmake curl build-essential git
5 git clone https://github.com/neovim/neovim
6 cd neovim
7 git checkout stable
8 make CMAKE_BUILD_TYPE=RelWithDebInfo
9 make CMAKE_EXTRA_FLAGS="-DCMAKE_INSTALL_PREFIX=$HOME/neovim"
10 cd build && cpack -G DEB && sudo dpkg -i nvim-linux-x86_64.deb
11 export PATH="$HOME/neovim/bin:$PATH"
```

### Uninstall

There is a CMake target to uninstall after make install:

```console
sudo cmake --build build/ --target uninstall
```

Alternatively, just delete the CMAKE_INSTALL_PREFIX artifacts:

```console
sudo rm /home/cory/neovim
```

### Installing Node.js for tree-sitter-cli

```console
sudo apt install nodejs npm
sudo npm install -g tree-sitter-cli
```
