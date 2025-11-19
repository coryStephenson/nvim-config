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
