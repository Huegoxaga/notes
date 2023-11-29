# MacOS

## zsh

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

## System-wide setting

### Power Settings

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

### Dock Settings

- `defaults write com.apple.dock autohide -bool true` turn off autohide
  - Or, press `Cmd+Alt+D`
  - By default, `defaults write com.apple.dock autohide -bool false`
- `defaults write com.apple.dock autohide-delay -float 1000` turn on autohide delay
  - By default, `defaults delete com.apple.dock autohide-delay`
- `defaults write com.apple.dock no-bouncing -bool TRUE` turn off the app icon's bouncing animation
  - By default, `defaults write com.apple.dock no-bouncing -bool FALSE`
- `defaults write com.apple.dock tilesize -float 1` change the dock size to 1 pixel
- Run `killall Dock` to restart the dock and load the new settings

### GateKeeper

- Disable GateKeeper, `sudo spctl --master-disable` to open applications from any sources without warnings
- `sudo xattr -d com.apple.quarantine <PathToApp>` remove quarantine flag of the app when system failed to open it and suggest the app is damaged

## Xcode Command Line Tools

- It includes and enables many useful command.
  - can be found at `/Library/Developer/CommandLineTools/usr/bin`
  - Command from the tools will be available at `/usr/bin`
- run `xcode-select --install` to install
  - Reinstall this tool when see `invalid active developer path (/Library/Developer/CommandLineTools)` error after OS update
  - `xcode-select --reset` if install command not working
- Located in `/Library/Developer/CommandLineTools`
  - run `sudo rm -rf /Library/Developer/CommandLineTools`, then `sudo xcode-select --install` to update, if update option does not show up in System Preferences
- Xcode includes this command-line tools. If it is installed on your system separately, uninstall the command-line tools.
  - Delete the `CommandLineTools` folder to uninstall the command line tools.
- run `xcode-select --print-path` to find out what version of Xcode is being used by the tools
- run `sudo xcode-select -switch /Applications/XcodeX.X.X/Xcode.app` set the default version of Xcode to use for the command-line tools.

## iCloud

- add `.nosync` after file or folder name will stop syncing the file to iCloud
  - `.nosync` can be added directly before or after the file's extension. e.g. `movie.nosync.avi` or `movie.avi.nosync`

## Homebrew

- It is the package management tool for macOS.
  - It provides many up-to-date GNU software that can replace the default Unix BSD software.
- Homebrew requires `Xcode Command Line Tools`
- Go to [Homebrew Site](https://brew.sh) and search for the package name for installation
- Install homebrew by running `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`.
- Uninstall homebrew by running `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall.sh)"`.
  - This will remove all the packages installed by homebrew as well.
- In Homebrew, a Formulae is a package which can be a command line tool. A Cask is an GUI App.
  - Installed command tools are located in the `/usr/local/Cellar` folder, they will have alias in the `/user/local/opt` folder.
    - run `brew --prefix <package>` to get the path of a package
  - Installed Apps are located in the `/Applications/`folder, they will have alias in the `/usr/local/Caskroom` with additional metadata.
- `brew search` list all packages available from homebrew.
- `brew update` update Homebrew and its package listings
- `brew outdated` list all outdated packages and apps
- `brew upgrade` update all outdated unpinned packages and apps installed via Homebrew
  - `brew pin <PackageName>` stop a package from being updated
  - `brew unpin <PackageName>` undo pinning
- `brew cleanup` Remove stale lock files and outdated downloads for all formulae and casks, and remove old versions of installed formulae
- `brew list` list installed packages and apps
- `brew install <PackageName>` install a package.
  - brew with distinguish some new package with pre-installed system package by prepending a `g` to its name. use `-with-default-names` will make them use their original names.
- `brew link <PackageName>` creates symlinks from `/usr/local/Cellar` to `/usr/local/bin`, or `/usr/local/lib`
  - unlinked packages are refered as keg-only
  - `brew unlink <package> && brew install <package>@NewVersion && brew link --overwrite <package>@NewVersion && brew pin <package>` downgrade a package to a specific version
    - Optionally, delete the unlinked latest package, instead of pinning it
  - `brew link --overwrite <PackageName>` update link
- `brew uninstall <PackageName>` uninstall a package.
- `brew home <PackageName>` open package or app homepage in browser.
- `brew tap <RepoName>` include an external repo. If a certain formulae is not found using `brew search`. The package can then be installed using `brew install`.
  - `brew update-reset` reset tap records, or delete the `Taps` folder records will be auto installed when needed
  - Taps are local copy of Git repos for Formulae and/or commands, located at `/usr/local/Homebrew/Library/Taps/homebrew/`
- `brew doctor` run self diagnoses
- `brew info <PackageName>` view the info for a package or app
- `brew deps --tree --installed` show installed packages and all their dependencies in tree
- `brew leaves` List installed formulae that are not dependencies of another installed formula
- For all the above command use `--cask` for cask only, use `--formula` for formulas only
  - `brew cask` is deprecated
- `brew install --appdir="/<PathToAppFolder>" <AppName>` specify the app folder

### Homebrew Services

- It can be used to manage brew installed packages that contains background services
- `brew tap homebrew/services` will be executed when any `brew services` command is entered
- `brew services list` list all services
- `brew services run <service>` Run the service formula without registering to launch automatically
- `brew services start <service>` Start the service formula immediately and register it to launch automatically
- `brew services stop <service>` Stop the service formula immediately and unregister it from launching automatically
- `brew services restart <service>` Stop (if necessary) and start the service formula immediately and register it to launch automatically
- `brew services cleanup` Remove all unused services
- The specific service in the above command can be replaced by a `--all` flag
- For launch registration:
  - If `sudo` is passed, operate on `/Library/LaunchDaemons` (started at boot).
  - If `sudo` is not used, operate on `~/Library/LaunchAgents` (started at login).

## Disk Management

- When erease external disks with `Disk Utility`, format it in `exFAT` format with `Master Boot Record` scheme allows it to be readable by both Mac and Window hosts
  - `FAT32` doesn't support files larger than 4 GB
  - For Mac, files stored in NTFS-formatted drives are read-only
  - `GUID Partition Map` is the new Mac scheme
  - `Apple Partition Map` is the old Mac scheme
- `diskutil partitionDisk /dev/<diskID> 4 <MBR|GPT> exfat "Files" 30% exfat "Windows" 40% exfat "Linux" 25% fat32 "RESCUE" 5%`
  - `MBR` is Master Boot Record
  - `3` is the number of partition
- `diskutil list` list all storage devices

### Clean up

- Clean App Caches under `~/Library/Application Support/<App Name>`, e.g.
  - Remove Webex support folders `WebEx Meetings` and `WebEx Folder` at `~/Library/Application\ Support/`
  - For VS Code, delete `Cache` and `CacheData` folders at `~/Library/Application\ Support/Code`, then in app command input enter `Clear Editor History`
  - For MS Teams, `rm -r ~/Library/Application\ Support/Microsoft/Teams`
- Clear App logs in `~/Library/Logs` folder
- Clean conda package caches, run `conda clean -f && conda clean -a`
- Homebrew clean up all broken symlinks `brew doctor && brew cleanup`
- Clean up npm cache `npm cache clean --force`
- Clean up sandboxed apps in folders located under `~/Library/Containers/`, usually can be achived by using apps' own clearing cache feature
- Clean up shared libraries for uninstalled apps under `~/Library/Application\ Support`

## Editor

### VSCode

#### Installation

- run `brew install --cask visual-studio-code` to install
- VSCode stores files at the following locations:
  - `/Applications/Visual Studio Code.app`
  - `~/Library/Preferences/com.microsoft.VSCode.helper.plist`
  - `~/Library/Preferences/com.microsoft.VSCode.plist`
  - `~/Library/Caches/com.microsoft.VSCode`
  - `~/Library/Caches/com.microsoft.VSCode.ShipIt/`
  - `~/Library/Application\ Support/Code/`
  - `~/Library/Saved\ Application\ State/com.microsoft.VSCode.savedState/`
  - `~/.vscode/`
- Sign in to sync all setup to newly installed editor
- Workspace is an environment that collects one or more project folders into one place shown in the sidebar
- Setting Scopes, VSCode settings have different scopes
  - User Settings - Settings that apply globally to any instance of VS Code you open, config file is located at `~/Library/Application Support/Code/User/settings.json`
  - Workspace Settings - Settings that override the global settings and only valid for the current workplace, the config is stored in the workspace's `.code-workspace` file
  - Folder Settings - Settings valid for a specific folder under a workspace, config file located in the `.vscode` under that folder

#### CLI

- `code` command is enabled using link after installation `/usr/local/bin/code -> /Applications/Visual Studio Code.app/Contents/Resources/app/bin/code`
- `code` launch vscode
  - `code .` launch vscode with the current folder open in a new window
  - `code <file>` open a file with vscode
  - `code --add <dir>` Add folder(s) to the last active window for a multi-root workspace
- `code --list-extensions` list installed extensions

#### Shortkeys

- `Shift + Command + P` open command pallet
- `Command + J` toggle terminal
- `Command + B` toggle sidebar

#### Debug

- VSCode will start a debug session by clicking the `Run and Debug` button in the debugger tab
- A customized debug config can be defined in the `launch.json` in the `.vscode` folder for a project
- Debug config can be platform-specific properties

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "program": "${workspaceFolder}/node_modules/gulp/bin/gulpfile.js",
      "args": ["myFolder/path/app.js"],
      "windows": {
        "args": ["myFolder\\path\\app.js"]
      }
    }
  ]
}
```

- There are also compound launch configurations

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Server",
      "program": "${workspaceFolder}/server.js"
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Client",
      "program": "${workspaceFolder}/client.js"
    }
  ],
  "compounds": [
    {
      "name": "Server/Client",
      "configurations": ["Server", "Client"],
      "preLaunchTask": "${defaultBuildTask}"
    }
  ]
}
```

#### Tasks

- VSCode can auto detect the project file and provide a list of auto-generated tasks when entering `Task: Run Task` in the command pallet
- User defined tasks can be written in the `tasks.json` in the `.vscode` folder for a project after entering `Task: Config Task` in the command pallet
- A custom task can be defined as:

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Run tests",
      "type": "shell",
      "command": "./scripts/test.sh",
      "windows": {
        "command": ".\\scripts\\test.cmd"
      },
      "group": "test",
      "presentation": {
        "reveal": "always",
        "panel": "new"
      }
    }
  ]
}
```

- Tasks can also be compounded

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Client Build",
      "command": "gulp",
      "args": ["build"],
      "options": {
        "cwd": "${workspaceFolder}/client"
      }
    },
    {
      "label": "Server Build",
      "command": "gulp",
      "args": ["build"],
      "options": {
        "cwd": "${workspaceFolder}/server"
      }
    },
    {
      "label": "Build",
      "dependsOn": ["Client Build", "Server Build"]
    }
  ]
}
```

## Automator

- It can be used to create document that run a certain task
- An automator document defines the tasks and triggers the tasks in different ways:
  - `Workflow` - tasks will be triggered from the Automator App
  - `Application` - Automator will create an app for the tasks, files can be dragged onto the app as input
    - Update the `Contents/Resources/ApplicationStub.icns` file to change teh app icon
    - The icon in the `Get Info` tab can be selected and copied, the paste it onto the icon of the new app in its `Get Info` tab
  - `Quick Action` - tasks will be available in dropdown menus
  - `Folder Action` - tasks will be triggered when items added to a specific folder
- Actions - Are the tasks that will be executed in order
- Variables - are stoted data that will be passed between actions
  - The `Varibales` tab can be used to declare or manage variables
  - Use `Set Value of Variable` action to store the output of the previous action into a variable
  - Drag the declared variables into actions for output

## Apple Script

- It can be used to mimic user's workflow in MacOS
- Scripts have extensioin `.scpt`
- `Script Editor` is its default editor

### Key Codes

- The keys on the keyboard will be described as codes in the script as below

![Key Codes](![NOT Gate](img/apple-script-key-codes.png))

### Syntax

- Example Script:

```scpt
tell application "Google Chrome" to activate
tell application "System Events"
  key code 17 using command down
  delay 0.5
  key code 37 using command down
  delay 1
  keystroke "https://www.instagram.com/users_account/"
  delay 0.5
  key code 36
  delay 2
end tell
```

#### Comment

- single line comment `-- This is a comment` or `# This is a comment`
- Multiline comments

```scpt
(* Hello world,
this is my first multi-line AppleScript
comment. *)
```

## Dual-Boot

- Boot Camp Assistant is the tool for setting up dual-boot for Windows on a Mac
- It will create a new partition using internal disk by default
- Boot Camp Assistant can be used to download all Mac hardware drivers for Windows
  - Open `Boot Camp Assistant`, go to menu bar and select `Action` and download Mac hardware drivers to be installed on Windows

### Dual-Boot on External Drive

- An EFI partition under GUID scheme is required for each OS to boot on Mac from most external drives
- To rename the EFI boot options during startup, put files generated by `sudo bless --folder <EDIDriveOutputPath> --label "<NewName>"` into the EFI drives `boot` folder
  - In window assign EFI partition a letter, unhide and copy the label files to `boot` folder

#### VM Disk Mapping Method(Recommended)

- Install other OSs on an external hard drive using the VM method
  1. Unmount the target disk's all partitions
     - find the disk ID using `diskutil list`
  2. Map a VirtualBox raw disk image to the entire disk, `sudo VBoxManage internalcommands createrawvmdk -filename "<PathToNewVMDK>" -rawdisk /dev/disk<ID>`
  3. Launch VirtualBox with elevated permissions, `sudo /Applications/VirtualBox.app/Contents/MacOS/VirtualBox`
  4. At the System tab, check the checkbox `Enable EFI (special OSes only)`
  5. Create a new Window virtual machine with existing virtual hard disk file, choose the `bootcamp.vwdk` file created in step `3`
  6. Mount the Windows ISO installation file to the VM, and start installation
     - Use custom install to setup partitions
     - prevent Windows Setup from automatically restarting by closing the VM window immediately when installation is completed and the restart progress bar shows up
  7. Restart Mac and hold `Option` key, select the Window drive to boot, finish the installation process
     - For Mac with T2 chip, disable secure boot in recovery mode
  8. Install the driver downloaded through Boot Camp Assistant

#### Bootable Installer Method

- Format in GUID scheme to boot
- For big OS with file size larger than 4GB, use `exFAT` instead
- The whole installer USB with master boot record is needed, not a single partition, use a separate external drive for the OS
- Steps for installing other OS on an external hard drive using the boot image method
  1. Download boot image builder, e.g. [unetbootin](https://unetbootin.github.io/)
  2. Select a `FAT32` formatted partition to burn the iso installation image
  3. Hold Option to boot into this image and install the OS into anther partition
  4. Boot into Window and install the drivers
- Ubuntu will install bootloader into Mac Drive's EFI partition, mount it using `diskutil` and delete the `BOOT` and `ubuntu` folder when uninstalling Ubuntu

#### WinToUSB

- A disk cloning software that runs on Windows
- It clones Window ISO into an external hard drive
- Use VM to run this software
- Select UEFI options and lagacy in the setting

#### Bootable Ubuntu

- Use Command Lines
  1. Download the image
  2. `hdiutil convert /path/to/ubuntu.iso -format UDRW -o /path/to/target.img`, remove the auto appended `.dmg` extension
  3. `diskutil unmountDisk /dev/diskN` unmount target drive
  4. `sudo dd if=/path/to/downloaded.img of=/dev/diskN bs=1m`
- Use Ethcher
  - Format target USB with GUID scheme and `FAT32`
- A partition can be selected for install during Ubuntu installation

## Security

### Free GPGMail

- `brew install --cask free-gpgmail`
- Follow installation guide on its [repo page](https://github.com/Free-GPGMail/Free-GPGMail)

## Troubleshoot

### Check Apple Service Status

- [Apple System Status Page](https://www.apple.com/uk/support/systemstatus/)
- [Apple System Status Page for Developers](https://developer.apple.com/system-status/)

### Reset SMC

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

### Reset NVRAM or PRAM

- NVRAM (nonvolatile random-access memory) is a small amount of memory that your Mac uses to store certain settings and access them quickly. PRAM (Parameter RAM) stores similar information
- It stores setting info like sound volume, display resolution, startup-disk selection, time zone, and recent kernel panic information
- corrupted NVRAM may prevent macOS from starting
- Settings can be viewed from `Applications > Utilities`, type `nvram -xp`, then press `Enter`
- Steps to reset NVRAM or PRAM:
  1. Shut down the Mac, then turn it on and immediately press and hold `Option + Command + P + R`
  2. release the keys after the second startup sound or logo appears and disappears for the second time

### Boot to Safe Mode

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

### Enter Recovery Mode

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
