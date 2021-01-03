# MacOS

### zsh

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

#### Power Settings

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

#### Dock Settings

- `defaults write com.apple.dock autohide -bool true` turn off autohide
  - Or, press `Cmd+Alt+D`
  - By default, `defaults write com.apple.dock autohide -bool false`
- `defaults write com.apple.dock autohide-delay -float 1000` turn on autohide delay
  - By default, `defaults delete com.apple.dock autohide-delay`
- `defaults write com.apple.dock no-bouncing -bool TRUE` turn off the app icon's bouncing animation
  - By default, `defaults write com.apple.dock no-bouncing -bool FALSE`
- `defaults write com.apple.dock tilesize -float 1` change the dock size to 1 pixel
- Run `killall Dock` to restart the dock and load the new settings

### Xcode Command Line Tools

- It includes and enables many useful command.
  - can be found at `/Library/Developer/CommandLineTools/usr/bin`
  - Command from the tools will be available at `/usr/bin`
- run `xcode-select --install` to install
- Located in `/Library/Developer/CommandLineTools`
  - run `sudo rm -rf /Library/Developer/CommandLineTools`, then `sudo xcode-select --install` to update, if update option does not show up in System Preferences
- Xcode includes this command-line tools. If it is installed on your system separately, uninstall the command-line tools.
  - Delete the `CommandLineTools` folder to uninstall the command line tools.
- run `xcode-select --print-path` to find out what version of Xcode is being used by the tools
- run `sudo xcode-select -switch /Applications/XcodeX.X.X/Xcode.app` set the default version of Xcode to use for the command-line tools.

### iCloud

- add `.nosync` after file or folder name will stop syncing the file to iCloud
  - `.nosync` can be added directly before or after the file's extension. e.g. `movie.nosync.avi` or `movie.avi.nosync`

### Homebrew

- It is the package management tool for macOS.
  - It provides many up-to-date GNU software that can replace the default Unix BSD software.
- Homebrew require `Xcode Command Line Tools`.
- Install homebrew by running `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`.
- Uninstall homebrew by running `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall.sh)"`.
  - This will remove all the packages installed by homebrew as well.
- In Homebrew, a Formulae is a package which can be a command line tool. A Cask is an GUI App.
  - Installed command tools are located in the `/usr/local/Cellar` folder, they will have alias in the `/user/local/opt` folder.
    - run `brew --prefix <package>` to get the path of a package
  - Installed Apps are located in the `/Applications/`folder, they will have alias in the `/usr/local/Caskroom` with additional metadata.
- `brew search` list all packages available from homebrew.
- `brew update` update all packages
- `brew outdated` list all outdated packages and apps
- `brew upgrade` update outdated packages and apps
- `brew cleanup` troubleshoot and clean old versions
- `brew list` list installed packages and apps
- `brew install <PackageName>` install a package.
  - brew with distinguish some new package with pre-installed system package by prepending a `g` to its name. use `-with-default-names` will make them use their original names.
- `brew uninstall <PackageName>` uninstall a package.
- `brew home <PackageName>` open package or app homepage in browser.
- `brew tap <RepoName>` include an external repo. If a certain formulae is not found using `brew search`. The package can then be installed using `brew install`.
  - `brew update-reset` reset tap records, or delete the `Taps` folder records will be auto installed when needed
  - Taps are local copy of Git repos for Formulae and/or commands, located at `/usr/local/Homebrew/Library/Taps/homebrew/`
- `brew doctor` run self diagnoses
- `brew info <PackageName>` view the info for a package or app
- `brew deps --tree --installed` show installed packages and all their dependencies in tree
- `brew leaves` List installed formulae that are not dependencies of another installed formula
- Install Apps with Casks with similar commands by using `brew cask`:
  - `brew cask install <AppName>` install an app
    - `brew install --appdir="/<PathToAppFolder>" <AppName>` specify the app folder

### Disk Cleanup

- Remove Wechat account folder at `/Users/<username>/Library/Containers/com.tencent.xinWeChat/Data/Library/Application Support/com.tencent.xinWeChat/`, then clear cache in app setting
- Remove Webex support folders `WebEx Meetings` and `WebEx Folder` at `/Users/<username>/Library/Application Support/`
- VS Code delete `Cache` and `CacheData` folders at `/Users/<username>/Library/Application Support/Code`, then in app command input enter `Clear Editor History`
- Clear VirtualBox log in `/Users/<username>/Library/VirtualBox` folder
- Clean conda package caches, run `conda clean -f && conda clean -a`
- Homebrew clean up`brew cleanup`
- Clean up npm cache `npm cache clean --force`

### Troubleshoot

#### Check Apple Service Status

- [Apple System Status Page](https://www.apple.com/uk/support/systemstatus/)
- [Apple System Status Page for Developers](https://developer.apple.com/system-status/)

#### Reset SMC

- System Management Controller(SMC) manages the following low level settings, even when the power is off:
  - Responding to presses of the power button
  - Responding to the display lid opening and closing on Mac notebooks
  - Battery management
  - Thermal management
  - SMS (Sudden Motion Sensor)
  - Ambient light sensing
  - Keyboard backlighting
  - Status indicator light (SIL) management
  - Battery status indicator lights
  - Selecting an external (instead of internal) video source for some iMac displays
- Currupt setting will cause bugs like fans that run constantly even when CPU usage isn’t high
- Reset step for laptop:
  1. Unplug the power, then shut down your Mac.
  2. Hold the left `Shift+Control+Option` keys down, then press and hold the power button down. Keep all four buttons pressed down for ten seconds, then let go.
  3. Plug the power cable back in, then turn on the Mac
- Reset step for Desktop Mac:
  1. Shut down your Mac, then unplug the power cable
  2. Wait 15 seconds
  3. Plug the power cord back in, then turn on the Mac

#### Reset NVRAM or PRAM

- NVRAM (nonvolatile random-access memory) is a small amount of memory that your Mac uses to store certain settings and access them quickly. PRAM (Parameter RAM) stores similar information
- It stores setting info like sound volume, display resolution, startup-disk selection, time zone, and recent kernel panic information
- corrupted NVRAM may prevent macOS from starting
- Settings can be viewed from `Applications > Utilities`, type `nvram -xp`, then press `Enter`
- Steps to reset NVRAM or PRAM:
  1. Shut down the Mac, then turn it on and immediately press and hold `Option + Command + P + R`
  2. release the keys after the second startup sound or logo appears and disappears for the second time

#### Boot to Safe Mode

- When Mac failed to boot up, try safe mode
  - When it happens during system upgrade, hold power key to turn it off
- Safe mode will perform the following during boot up:
  - Verifies your startup disk and attempts necessary repair directory issues
  - Loads kernel extensions required
  - Prevents automatic opening of startup and login items
  - Disables user-installed fonts
  - Deletes font, kernel, and other system cache files
- Steps to enter safe mode:
  - Start up an Intel-based Mac in safe mode
    - shut down Mac, then wait 10 seconds.
    - press power button, then immediately press and hold the `Shift` key.
    - Release the `Shift` key when the login window apprears
  - Start up a Mac with Apple silicon in safe mode
    - shut down Mac, then wait 10 seconds.
    - Press and hold the power button until the startup disks and Options appear.
    - Press and hold the Shift key, then click Continue in Safe Mode.
- Verify Safe Mode:
  - hold down the Option key and choose `Apple menu -> System Information`, see Boot Mode `Safe` in the Software section
- Leave Safe Mode, restart the machine normally

#### Enter Recovery Mode

- Recovery Mode provides the following features without boot up macOS:
  - `Restore from Time Machine`: Restore your files from a Time Machine backup
  - `Reinstall macOS`: Download and reinstall the Mac operating system
  - `Safari` (or Get Help Online): Use Safari to browse the web and find help for your Mac. Links to Apple's support website are included. Browser plug-ins and extensions are disabled
  - `Disk Utility`: Use Disk Utility to repair your disk or erase your disk or other storage device
    - Erase hard drive here, before reinstall macOS
  - Additional utilities are available from the Utilities menu in the menu bar, including `Startup Security Utility` (or Firmware Password Utility), and `Terminal`
- Turn on your Mac and immediately press and hold these two keys: Command (⌘) and R. Release the keys when you see an Apple logo, spinning globe
  - admin password is required to continue
  - spinning globe appears only when Mac can't start up from its built-in macOS Recovery system
  - To enter Internet Recovery Mode manully, use Key combo `Option-Command-R` or `Shift-Option-Command-R`
