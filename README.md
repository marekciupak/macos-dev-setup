# macOS dev environment setup

## Security

### Hard disc encryption

Go to `System preferences > Security & Privacy > FileVault` and make sure the FileVault is ON.

### Firewall

Go to `System preferences > Security & Privacy > Firewall` and make sure the Firewall is ON.

### More

https://blog.bejarano.io/hardening-macos.html

## Keyboard preferences

In `System preferences > Keyboard`:

  * `Key Repeat > Fast` (all the way to the right)
  * `Delay Until Repeat > Short` (all the way to the right)
  * `Modifier Keys... > Caps Lock (⇪) Key` set to `^ Control`

## Apps

#### Text editor

Install VS Code: https://code.visualstudio.com/

##### Configuration

Open VS Code, go to `Code` > `Preferences` > `Settings` and paste:

```yml
{
    "editor.rulers": [
        120
    ],
    "editor.tabSize": 2,
    "workbench.colorTheme": "One Monokai",
    "explorer.confirmDragAndDrop": false,
    "explorer.confirmDelete": false,
    "workbench.startupEditor": "newUntitledFile",
    "files.insertFinalNewline": true,
    "files.trimTrailingWhitespace": true,
    "files.trimFinalNewlines": true,
    "terminal.integrated.fontFamily": "Meslo LG S DZ for Powerline",
}
```

Install `One Monokai` extension.

#### Web browser

Install Chrome: https://www.google.com/chrome/browser/desktop/index.html

#### Terminal

Install iTerm2: https://www.iterm2.com/downloads.html

#### Software package manager

Install Homebrew: http://brew.sh/

#### Basic tools

Install some useful packages:

```shell
brew install curl mc gpg gpg2
```

#### Git

Install Git:

```shell
brew install git
```

Set you username and email in Git:

```shell
git config --global user.name "Mona Lisa"
git config --global user.email "email@example.com"
```

:warning: Don't forget to replace _"Mona Lisa"_ and _"email@example.com"_ with your own data.

#### Shell

Install [Zsh] and set it as a default shell:

```shell
brew install zsh zsh-completions
chsh -s /bin/zsh
```

:warning: Reopen terminal window now to load Zsh shell.

Install [Oh My Zsh]:

```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

#### Make your terminal look pretty

##### Use Dark Background in iTerm2

* Go to: `iTerm2 > Preferences > Profiles > Colors`
* Use `Color presets...` menu to import and select downloaded `Pastel (Dark Background)` theme

##### Install [Powerline Fonts]

```shell
cd $HOME
git clone https://github.com/powerline/fonts.git
./fonts/install.sh
rm -rf ~/fonts/
```

##### Set font in iTerm2

* Go to: `iTerm2 > Preferences > Profiles > Text > Font > Change Font`
* Select the font: `Fixed Width > Meslo LG S DZ for Powerline > RegularForPowerline > 11`

##### Set [zsh theme]

Edit `~/.zshrc` file and update `ZSH_THEME=` to:

```shell
ZSH_THEME="agnoster"
```

#### Configure Zsh

Install [zsh-autosuggestions]:

```shell
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

Edit `~/.zshrc` file and update `plugins=` to:

```shell
plugins=(git bundler osx rake ruby rails zsh-autosuggestions fasd)
```

:mortar_board: List of all available plugins is here: https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins.

Edit `~/.zshrc` file and the following lines at the end:

```shell
export EDITOR='vim'

DEFAULT_USER=`whoami`

HISTFILE=$HOME/.zsh_history
HISTSIZE=10000
SAVEHIST=10000
setopt APPEND_HISTORY           # append rather than overwrite history file.
setopt EXTENDED_HISTORY         # save timestamp and runtime information
setopt HIST_EXPIRE_DUPS_FIRST   # allow dups, but expire old ones when I hit HISTSIZE
setopt HIST_FIND_NO_DUPS        # don't find duplicates in history
setopt HIST_IGNORE_ALL_DUPS     # ignore duplicate commands regardless of commands in between
setopt HIST_IGNORE_DUPS         # ignore duplicate commands
setopt HIST_REDUCE_BLANKS       # leave blanks out
setopt HIST_SAVE_NO_DUPS        # don't save duplicates
setopt INC_APPEND_HISTORY       # write after each command
setopt SHARE_HISTORY            # share history between sessions

ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=30'

LC_CTYPE=en_US.UTF-8
LC_ALL=en_US.UTF-8
```

#### Vim

Install [Janus Vim Distribution]:

```shell
curl -L https://bit.ly/janus-bootstrap | bash
```

Map `jj` to `esc`:

```shell
echo ':imap jj <Esc>' >> ~/.vimrc.before
```

### Another apps I recommend

* [Alfred](https://www.alfredapp.com/)
* [Spectacle](https://www.spectacleapp.com/)
* [Monosnap](https://monosnap.com/welcome)

### RoR & web development

#### PostgreSQL

```shell
brew install postgresql
brew services start postgresql
```

#### Redis

```shell
brew install redis
brew services start redis
```

#### Node Version Manager

Install NVM: https://github.com/creationix/nvm

##### Install yarn

```shell
npm install -g yarn
```

#### Ruby version manager

Install RVM: https://rvm.io/rvm/install

[Zsh]: http://www.zsh.org/
[Oh My Zsh]: https://github.com/robbyrussell/oh-my-zsh
[Powerline Fonts]: https://github.com/powerline/fonts
[zsh theme]: https://github.com/robbyrussell/oh-my-zsh/wiki/Themes
[Solarized Theme]: http://ethanschoonover.com/solarized
[zsh-autosuggestions]: https://github.com/zsh-users/zsh-autosuggestions
[Janus Vim Distribution]: https://github.com/carlhuda/janus
