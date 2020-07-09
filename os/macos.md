# MacOS

### Zsh

- `Zsh` is the macOS default shell for its terminal. It is similar to `bash` but has the following difference.
- set `Zsh` as the default shell, run `chsh -s /bin/zsh` then restart the terminal.
- set `bash` as the default shell,run `chsh -s /bin/bash` then restart the terminal.
- The startup config files for `zsh`:
  - `.zshenv` is always sourced.
  - `.zprofile` is sourced before `.zshrc`
  - `.zshrc` is for interactive(non-login, sub-shell) shell configuration.
  - `.zlogin` is sourced on the start of a login shell after `.zshrc`.
  - `.zlogout` is sourced upon exiting.
- The startup config files can be created in the `/etc` folder or the `~/` folder.
  - Startup config files in `/etc` folder will be ran for all users.
  - Startup config files in `/~` folder will overwrite the same file in `/etc`.
- `/etc/.zprofile` uses `/usr/libexec/path_helper` to load paths.
  - `path_helper` load path text file in the `/etc/.paths` file and `/etc/paths.d` folder for command.
  - `path_helper` load path text file in the `/etc/.manpaths` file and `/etc/manpaths.d` folder for command maunals.
- run `manpath` to see all the command maunals text file path.
- `Oh My ZSH` Plugins, [Click here](https://github.com/ohmyzsh/ohmyzsh/wiki) for docs.
  - Installation, run `sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`
  - [Click here](https://github.com/ohmyzsh/ohmyzsh/wiki/themes) to find themes options.
  - Add `ZSH_THEME=themename` in `~/.zshrc` to change themes for terminal.
    - set `ZSH_THEME=""` to disable theme.

### System-wide setting

##### power settings

- run `pmset -g` list power settings for current power source.
- `hibernatemode`:
  - `0`: normal sleep, memory is always powered during sleep. default sleep mode for desktop Macs.
  - `1`: hibernate mode, memory is cached and not powered on disk during sleep. this is the default for pre-2005 laptops.
  - `3`: safe sleep, memory is cached on disk and powered during sleep. this is the default for laptops made after 2005.
  - `25`: hibernate mode, memory is cached and not powered on disk during sleep. the setting used for post-2005 laptops.
- `standby`:
  - `1`: let the machine enter hibernate mode from safe sleep after it has slept for a specified time period.
  - `0`: machine won't enter hibernate mode under any circumstances.
- `hibernatefile` - location for the memory image on disk.
- Change setting using the -a, -b, -c, -u flags. For example, `sudo pmset -a hibernatemode 25`
  - `-b`, apply to battery
  - `-c`, charger
  - `-u`, UPS
  - `-a`, all

### Xcode Command Line Tools

- It includes and enables many useful command.
  - can be found at `/Library/Developer/CommandLineTools/usr/bin`
  - Command from the tools will be available at `/usr/bin`
- run `xcode-select --install` to install
- Located in `/Library/Developer/CommandLineTools`
- Xcode includes this command-line tools. If it is installed on your system separately, uninstall the command-line tools.
  - Delete the `CommandLineTools` folder to uninstall the command line tools.
- run `xcode-select --print-path` to find out what version of Xcode is being used by the tools
- run `sudo xcode-select -switch /Applications/Xcode8.3.3/Xcode.app` set the default version of Xcode to use for the command-line tools.

### Homebrew

- It is the package management tool for macOS.
  - It provides many up-to-date GNU software that can replace the default Unix BSD software.
- Homebrew require `Xcode Command Line Tools`.
- Install homebrew by running `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`.
- Uninstall homebrew by running `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall.sh)"`.
  - This will remove all the packages installed by homebrew as well.
- In Homebrew, a Formulae is a package which can be a command line tool. A Cask is an GUI App.
  - Installed command tools are located in the `/usr/local/Cellar` folder, they will have alias in the `/user/local/bin` folder.
  - Installed Apps are located in the `/Applications/`folder, they will have alias in the `/usr/local/Caskroom` with additional metadata.
- `brew search` list all packages available from homebrew.
- `brew update` update all packages
- `brew outdated` list all outdated packages
- `brew upgrade` update outdated packages
- `brew cleanup` clean old versions
- `brew list` list installed packages
- `brew install <PackageName>` install a package.
  - brew with distinguish some new package with pre-installed system package by prepending a `g` to its name. use `-with-default-names` will make them use their original names.
- `brew uninstall <PackageName>` uninstall a package.
- `brew home <PackageName>` open package homepage in browser.
- `brew tap <RepoName>` include an external repo. If a certain formulae is not found using `brew search`. The package can then be installed using `brew install`.
- `brew doctor` run self diagnoses
- `brew info <PackageName>` view the info for a package.
- Install Apps with Casks with similar commands by using `brew cask`:
  - `brew cask install <AppName>` install an app
  - `brew cask list` list installed apps
    - `brew cask list <keyword>` search app
  - `brew cast home <PackageName>` open app homepage in browser.
  - `brew cask info <AppName>` view the info for an app.
  - `brew cask upgrade` view the info for an app.
  - `brew cask outdated` view the info for an app.
