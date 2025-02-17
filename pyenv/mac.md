# Setting Up `pyenv` on MacOS

## Prerequisites

Before installing `pyenv` on macOS, you need to install several dependencies:

### Install Xcode Command Line Tools

To install the Xcode command line tools, run:

```sh
xcode-select --install
```

### Install Required Libraries

Since `pyenv` builds Python versions from source, you need additional libraries for the build process. These can be installed via Homebrew:

```sh
brew install openssl readline sqlite3 xz zlib
```

## Installing pyenv

There are two ways to install `pyenv` on macOS:

### Method 1: Using Homebrew

1. Update Homebrew and install `pyenv`:

   ```sh
   brew update
   brew install pyenv
   ```

2. Add `pyenv` to your shell initialization file (for `zsh` users, update `~/.zshrc`):

   ```sh
   echo 'eval "$(pyenv init --path)"' >> ~/.zshrc
   ```

### Method 2: Installing from GitHub

1. Clone the `pyenv` repository to your home directory:

   ```sh
   git clone https://github.com/pyenv/pyenv.git ~/.pyenv
   ```

2. Add the following lines to your shell initialization file:

   ```sh
   echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
   echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
   echo 'eval "$(pyenv init --path)"' >> ~/.zshrc
   ```

## Managing Python Versions with pyenv

### Installing a Python Version

To install a specific Python version, use:

```sh
pyenv install [PYTHON_VERSION]
```

To list all available Python versions:

```sh
pyenv install -l
```

### Viewing Installed Versions

To see which Python versions are installed on your system:

```sh
pyenv versions
```

The currently active version will have an asterisk (`*`) next to it.

### Checking the Active Python Version

To check which Python version is currently active in your shell:

```sh
pyenv version
```

### Setting the Global Python Version

To set a default Python version for all new terminal sessions:

```sh
pyenv global [PYTHON_VERSION]
```

Alternatively, you can set the environment variable manually:

```sh
export PYENV_VERSION=[PYTHON_VERSION]
```

### Setting a Local Python Version for a Project

To specify a Python version for a particular project directory:

```sh
pyenv local [PYTHON_VERSION]
```

This command creates a `.python-version` file inside the project directory.

## Creating Virtual Environments

Virtual environments allow you to manage dependencies on a per-project basis.

### Creating a Virtual Environment

1. Navigate to your project directory and set the desired Python version:

   ```sh
   pyenv local [PYTHON_VERSION]
   ```

2. Create a virtual environment:

   ```sh
   python -m venv .venv
   ```

### Activating the Virtual Environment

To activate the virtual environment:

```sh
source .venv/bin/activate
```

For Windows PowerShell:

```sh
.\.venv\Scripts\activate
```

Once activated, your command prompt will show a `(.venv)` prefix.

### Deleting and Recreating a Virtual Environment

If you need to reset your virtual environment, delete the `.venv` directory and recreate it:

```sh
rm -rf .venv
python -m venv .venv
```

## Additional Resources

For a complete list of `pyenv` commands, refer to the [pyenv Command Reference](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md).

---

By following these steps, you will have `pyenv` successfully set up on your macOS system, allowing you to manage multiple Python versions efficiently.

