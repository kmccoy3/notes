
# Homebrew

### Basic Brew Command Syntaxes
```
## See if Homebrew is working:
$ brew doctor

## Update Homebrew:
$ brew update

## View installed programs needing updates:
$ brew outdated

## Update Homebrew and installed programs:
$ brew upgrade

## Upgrade only the program named nmap:
$ brew upgrade nmap

## To search for all Google apps available from Homebrew:
$ brew search google

## Download and install a program called “nmap”:
$ brew install nmap

## Remove the program “nmap”:
$ brew remove nmap

## Show what Homebrew programs are installed:
$ brew list

## To list old versions:
$ brew cleanup -n

## To remove old versions:
$ brew cleanup
```

### Cask Syntax
```
## Simply add "cask" after "brew" command
$ brew cask install google-earth-pro
```

### MAS syntax
```
## List all apps installed:
$ mas list

## Show all apps with pending updates:
$ mas outdated

## Update all apps:
$ mas upgrade

## Search for an app in the App Store:
$ mas search

## Install app (need app number)
$ mas install application number
```

