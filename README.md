# Colin's Mac M1 setup documents

## Intro

Documentation of my setup steps for Mac M1

## Rosetta

Notes: Apple is planning to remove Rosetta 2 when the transition to Apple Silicon is completed. But until then, most of the tools should be transitioned to Apple Silicon as well.

An emulator called Rosetta 2 that allows us to run apps that use x86 instructions, the instruction set used by Intel chips, on ARM.

```console
/usr/sbin/softwareupdate --install-rosetta --agree-to-license
```

The `--agree-to-license flag` will skip the interactive install and agree to Apple’s license. But, if you want to investigate what you’re signing up for, feel free to delete the flag and give the license a read.

## Homebrew

Run to install

```console
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)
```

## Tools

Check the `brew-installs.sh` folder before doing this and edit it to whatever you want. Update the

```json
{
  "Working Directory": "/Users/cokearns"
}
```

node in both json profiles with your user name, if not sure run:

```console
whoami
```

to see.

To run script:

```console
./brew-installs.sh
```

## Iterm2

The previous script installs it, you can now use it for remainder.

## Oh My Zsh

Plugin manager for terminal

To download:

```console
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

For syntax highlighting:

```console
cd $HOME/.oh-my-zsh/plugins

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git

echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
```

## NVM

Node package mananger for easy switching, a must always install node with it or you will regret later!

```console
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
```

```console
export NVM_DIR="$HOME/#.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

To get the latest stable node version:

```console
nvm install --lts
nvm use lts
```

## Git and GitHub

**_Replace username and email variables_**

```console
git config --global user.name {{USERNAME}} &&
git config --global user.email {{EMAIL}} &&
git config --global --list
```

## Unhide Dot files

```console
defaults write com.apple.Finder AppleShowAllFiles true
```

for finder
`ls -a` will list them in terminal but you will have to use everytime

## VS CODE

Turn on settings sync if personal settings are synced on github, it can sync preferences extensions themes and keyboard shortcuts etc, do not sync with work settings if too specialized, I do not :)
I have included the settings file I currently have, above, but for myself I can just sync. These sync will include my Prettier formating set up with ESLINT for angular and react projects.

After installing prettier, make it default formatter over ESlint if you want, also if you want, you can have it format on save, add these to the VSCODE settings.json (shouldnt need if it has been synced)

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.formatOnPaste": true
}
```

## Powerlevel 10

Follow instructions to install with OhMyZsh, it will give you extra features. Instrcutions are here:

<https://github.com/romkatv/powerlevel10k/#oh-my-zsh>

Install pure theme if you want, it mimics the pure package manager theme. Do not install pure itself but follow the instructions below for theme.

<https://gist.github.com/romkatv/7cbab80dcbc639003066bb68b9ae0bbf>

## Git config updates

**_I do this, but be careful with it, this will default git to push to origin and current branch with just `git push` and no arguments, but be careful if you could be pushing to master :)_**

```console
git config --global push.default current
```

Generate SSH key and add to github.
<https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account>
