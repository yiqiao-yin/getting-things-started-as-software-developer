# Setting Up `pyenv` on Windows

## Prerequisites

Before installing `pyenv` on Windows, you need to install a few dependencies:

### Install Git for Windows

Download and install Git for Windows from the official website:

[Git for Windows](https://gitforwindows.org/)

Ensure that Git is added to your system's `PATH` during installation.

### Install Visual Studio Build Tools

Download and install the Visual Studio Build Tools to provide the necessary compilers for building Python versions:

[Visual Studio Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)

During installation, ensure that the following components are selected:
- Windows 10 SDK
- C++ x64/x86 build tools

## Installing pyenv

`pyenv` for Windows can be installed using `pyenv-win`, a Windows-compatible version of `pyenv`.

### Install pyenv-win via PowerShell

1. Open PowerShell and run the following command:

   ```sh
   Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://pyenv.run')
   ```

2. This script will install `pyenv-win` and configure your system environment variables automatically.

3. Restart your terminal or run the following command to refresh your environment variables:

   ```sh
   refreshenv
   ```

## Configuring Environment Variables

Ensure the following paths are added to your system's `PATH` variable:

```sh
%USERPROFILE%\.pyenv\pyenv-win\bin
%USERPROFILE%\.pyenv\pyenv-win\shims
```

To verify the installation, run:

```sh
pyenv --version
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
set PYENV_VERSION=[PYTHON_VERSION]
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

To activate the virtual environment in PowerShell:

```sh
.\.venv\Scripts\Activate
```

Once activated, your command prompt will show a `(.venv)` prefix.

### Deleting and Recreating a Virtual Environment

If you need to reset your virtual environment, delete the `.venv` directory and recreate it:

```sh
rm -rf .venv
python -m venv .venv
```

## Additional Resources

For a complete list of `pyenv` commands, refer to the [pyenv-win GitHub repository](https://github.com/pyenv-win/pyenv-win).

---

By following these steps, you will have `pyenv` successfully set up on your Windows system, allowing you to manage multiple Python versions efficiently.

