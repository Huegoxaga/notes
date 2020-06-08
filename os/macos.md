# MacOS

### Xcode Command Line Tools

- It includes and enables many useful command.
  - can be found at `/Library/Developer/CommandLineTools/usr/bin`
- run `xcode-select --install` to install
- Located in `/Library/Developer/CommandLineTools`
- Xcode includes this command-line tools. If it is installed on your system separately, uninstall the command-line tools.
  - Delete the `CommandLineTools` folder to uninstall the command line tools.
- run `xcode-select --print-path` to find out what version of Xcode is being used by the tools
- run `sudo xcode-select -switch /Applications/Xcode8.3.3/Xcode.app` set the default version of Xcode to use for the command-line tools.
