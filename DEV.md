# Dev Configuration

Note this setup is personal, and will likely have personal dependencies and customizations.

## homebrew

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## yadr + zsh

```
sh -c "`curl -fsSL https://raw.githubusercontent.com/skwp/dotfiles/master/install.sh`"
chsh -s $(which zsh)
```

## nginx

Since `/usr/local/etc/nginx` didn't come over in my TimeMachine upgrade, lets symlink our servers directory so we don't lose our nginx configs again.

```
brew install nginx
cd /usr/local/etc/nginx/
rm servers
ln -s /Volumes/dev/servers
```

## sshfs

```
brew cask install osxfuse
brew install sshfs
```

## azure
```
brew install azure-cli
```