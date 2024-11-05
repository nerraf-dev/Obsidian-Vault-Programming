 **An Alternative to NVM: Fast Node Manager (fnm)**

**Introduction**: Looking for a [Node.js](https://node.js/?form=MG0AV3) version manager that works cross-platform and is incredibly fast? Fast Node Manager (fnm) might just be the tool you need.

**1. Why fnm?** I’ve previously used [Node Version Manager (NVM)](https://github.com/nvm-sh/nvm?form=MG0AV3)  on macOS and Linux machines, but recently switched back to using my Windows machine. 
While there is a [NVM for Windows](https://github.com/coreybutler/nvm-windows?form=MG0AV3), I noticed that the [Node.js](https://node.js/?form=MG0AV3) installation instructions used something called `fnm`.

**2. What is fnm?** Fast Node Manager (fnm) is a [Node.js](https://node.js/?form=MG0AV3) version manager, designed to be lightweight and efficient due to its development in Rust. Unlike `nvm`, which provides more features such as support for multiple languages and global binaries, `fnm` focuses on providing a simple and fast [Node.js](https://node.js/?form=MG0AV3) version manager.

**3. Commands Overview**: `fnm` comes with familiar commands for version and package management:

```sh
Commands:
  list-remote  List all remote Node.js versions [aliases: ls-remote]
  list         List all locally installed Node.js versions [aliases: ls]
  install      Install a new Node.js version [aliases: i]
  use          Change Node.js version
  env          Print and set up required environment variables for fnm
  completions  Print shell completions to stdout
  alias        Alias a version to a common name
  unalias      Remove an alias definition
  default      Set a version as the default version
  current      Print the current Node.js version
  exec         Run a command within fnm context
  uninstall    Uninstall a Node.js version [aliases: uni]
  help         Print this message or the help of the given subcommand(s)
```

You can find more details on the [commands and options](https://github.com/Schniz/fnm/blob/master/docs/commands.md?form=MG0AV3).

**4. Getting Started with fnm**: It's probably best to uninstall any previous [Node.js](https://node.js/?form=MG0AV3) versions before getting started.

**Installation**:

- **Windows**: Install using `winget` by running the following in PowerShell:   
    ```sh
    winget install Schniz.fnm
    ```
    
- **Linux/macOS**: The easiest option is to use the install script:
    ```sh
    curl -fsSL https://fnm.vercel.app/install | bash
    ```
    

**Shell Setup**: Once installed, the shell needs setting up. If the install script wasn't run, then follow these steps:

- **Bash**:
    ```sh
    eval "$(fnm env --use-on-cd --shell bash)"
    ```
    
- **Zsh**:
    ```sh
    eval "$(fnm env --use-on-cd --shell zsh)"
    ```
    

**Windows/PowerShell**: After installation, open a new PowerShell window. If `fnm` is not recognized, run:
```sh
fnm env --use-on-cd --shell powershell | Out-String | Invoke-Expression
```

**5. Managing [Node.js](https://node.js/?form=MG0AV3) Versions with fnm**:

- **Check installed [Node.js](https://node.js/?form=MG0AV3) versions**:    
    ```sh
    fnm list
    ```
    
- **See available [Node.js](https://node.js/?form=MG0AV3) versions for download**:
    ```sh
    fnm list-remote
    ```
    
- **Install a specific version** (e.g., version 20):
    ```sh
    fnm install 20
    ```
    
- **Install the latest version** (e.g., version 22):
    ```sh
    fnm install 22
    ```
    
- **Install a specific version by number** (e.g., 19.8.1):
    ```sh
    fnm install 19.8.1
    ```
    
- **Use a specific version**:
    ```sh
    fnm use 20
    ```
    
- **Download and use [Node.js](https://node.js/?form=MG0AV3) in one go**:
    ```sh
    fnm use --install-if-missing 22
    ```
    

Using `fnm` makes managing [Node.js](https://node.js/?form=MG0AV3) versions a breeze. Whether you're switching between projects with different requirements or just want to try out the latest features, `fnm` has you covered.