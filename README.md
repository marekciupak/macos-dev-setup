# macOS dev environment setup

## Security

### Disc encryption

Go to `System preferences > Security & Privacy > FileVault` and make sure the FileVault is ON.

### Firewall

Go to `System preferences > Security & Privacy > Firewall` and make sure the Firewall is ON.

## Keyboard preferences

In `System preferences > Keyboard`:

* `Key Repeat > Fast` (all the way to the right)
* `Delay Until Repeat > Short` (all the way to the right)
* `Modifier Keys... > Caps Lock (⇪) Key` set to `^ Control`

## Apps

Install Atom: https://atom.io/

Install Chrome: https://www.google.com/chrome/browser/desktop/index.html

Install terminal iTerm2: https://www.iterm2.com/downloads.html

Install software package manager Homebrew: http://brew.sh/

`brew install curl git mc gpg gpg2`

`brew install zsh zsh-completions && chsh -s /bin/zsh`

`sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`

Install [Powerline Fonts]:
* `cd $HOME`
* `git clone https://github.com/powerline/fonts.git`
* `./fonts/install.sh`

Set font in iTerm2 to Meslo, for ex.:

`Fixed Width > Meslo LG S DZ for Powerline > RegularForPowerline > 11`

Use [Solarized Theme] in iTerm2:
* Download http://ethanschoonover.com/solarized/files/solarized.zip
* Unpack
* Import and select theme in iTerm2

Make sure you have following lines in `~/.zshrc` file:

```shell
# Path to your oh-my-zsh installation.
export ZSH=$HOME/.oh-my-zsh

# Set name of the theme to load.
# Look in ~/.oh-my-zsh/themes/
# Optionally, if you set this to "random", it'll load a random theme each
# time that oh-my-zsh is loaded.
ZSH_THEME="agnoster"

plugins=(git bundler osx rake ruby rails zsh-autosuggestions fasd)

source $ZSH/oh-my-zsh.sh
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

export PATH="$PATH:$HOME/.rvm/bin" # Add RVM to PATH for scripting

ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=30'

LC_CTYPE=en_US.UTF-8
LC_ALL=en_US.UTF-8
```

Install tmux:

`brew install tmux`

My `~/.tmux.conf`:

```
# C-b is not acceptable -- Vim uses it
set-option -g prefix C-a
bind-key C-a last-window

# Allows us to use C-a a <command> to send commands to a TMUX session inside
# another TMUX session
bind-key a send-prefix

# Start numbering at 1
set -g base-index 1

# color
set -g default-terminal "screen-256color"

# status bar
set-option -g status-utf8 on

# Enable Scrolling with mouse
#setw -g mode-mouse on

# Enable Scrolling with mouse through history as well
set -g terminal-overrides 'screen-256color:smcup@:rmcup@'

#### COLOUR (Solarized dark)

# default statusbar colors
set-option -g status-bg black #base02
set-option -g status-fg yellow #yellow
set-option -g status-attr default

# default window title colors
set-window-option -g window-status-fg brightblue #base0
set-window-option -g window-status-bg default
#set-window-option -g window-status-attr dim

# active window title colors
set-window-option -g window-status-current-fg brightred #orange
set-window-option -g window-status-current-bg default
#set-window-option -g window-status-current-attr bright

# pane border
set-option -g pane-border-fg black #base02
set-option -g pane-active-border-fg brightgreen #base01

# message text
set-option -g message-bg black #base02
set-option -g message-fg brightred #orange

# pane number display
set-option -g display-panes-active-colour blue #blue
set-option -g display-panes-colour brightred #orange

# clock
set-window-option -g clock-mode-colour green #green
```

Install Janus Vim Distribution: https://github.com/carlhuda/janus

Another apps I recommend:
* Alfred 2
* Spectacle 2
* Monosnap

## RoR & web development

`brew install postgresql && brew services start postgresql`

`brew install redis && brew services start redis`

To launch PostgreSQL and Redis automatically on system startup:
* `ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents`
* `ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents`

`brew install node`

Install Ruby version manager: https://rvm.io/rvm/install

[Powerline Fonts]: https://github.com/powerline/fonts
[Solarized Theme]: http://ethanschoonover.com/solarized
