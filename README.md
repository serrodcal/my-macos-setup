# My MacOS setup

Repo with my MacOS setup

## What are we going to configure?

* zsh
* Oh my zsh!
* Fonts and zsh theme
* Homebrew
* Dotfiles

## Check zsh as default

Go to `Users and groups` > left click on the current user > Advanced Options > `login shell` > set as `/bin/zsh`.

## Homebrew installation

Run the following command:

```sh
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then, install Cask:

```sh
$ brew install cask
```

## Install Oh my zsh!

Run the following command:

```sh
$ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Install git

Run the following command:

```sh
$ brew install git
```

Then, let's create a folder to store all the repositories:

```sh
$ mkdir Repositories
```

## Install fonts

Go to `~/repositories` and then, create a new folder:

```sh
$ cd ~/Repositories
$ mkdir github
$ cd github
```

Run the following commands:

```sh
$ git clone https://github.com/powerline/fonts.git
$ cd fonts
$ ./install.sh
```

**Note**: just in case P10K is needed, please use below ([link](https://github.com/romkatv/powerlevel10k/blob/master/README.md#how-was-the-recommended-font-created)):

```sh
git clone --depth=1 https://github.com/romkatv/nerd-fonts.git
cd nerd-fonts
./build 'Meslo/S/*'
```

## Clone my MacOS setup

Run the following commands:

```sh
$ cd ~/Repositories/github/
$ mkdir serrodcal
$ cd serrodcal
$ git clone https://github.com/serrodcal/my-local-setup.git
```

## Change Terminal theme

Import the new one (i.e. from `my-local-setup` repository) in Terminal preferences.

## Install powerlevel10k

Download from https://github.com/romkatv/powerlevel10k#fonts and install them using double-click.

Then, run the following commands:

```sh
$ brew install romkatv/powerlevel10k/powerlevel10k
$ echo "source $(brew --prefix)/opt/powerlevel10k/powerlevel10k.zsh-theme" >>~/.zshrc
````

## Choose the proper font

Go to `Terminal > Preferences > Profiles` and choose `Meslo LG S NF for Powerline as regular and size 13`.

## Add alias to full update and clean up Homebrew

Add the following line to `~/.zshrc` file:

```
alias breu="brew update && brew upgrade && brew upgrade --cask && brew cleanup -s"
```

## Install SDKman

Run the following commands:

```sh
$ curl -s "https://get.sdkman.io" | bash
```

Follow the instructions on-screen to complete installation. Next, open a new terminal or enter:

```sh
$ source "$HOME/.sdkman/bin/sdkman-init.sh"
```

## Install podman:

Run the following commands:

```sh
$ brew install podman
$ brew install docker-compose
```

Now, let's create a new machine and start the service:

```sh
$ podman machine init
$ podman machine start
```

Next, add the alias to `~/.zshrc` file:

```
alias docker="podman"
```

## Generate SSH key for Github

Run the following commands:

```sh
$ ssh-keygen -t ed25519 -C "email@example.com"
$ pbcopy < ~/.ssh/id_ed25519.pub
```
