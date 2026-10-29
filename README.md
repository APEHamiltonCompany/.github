# .github
# Development Environment Setup Guide

General-purpose setup for new users joining an `APEHamiltonCompany` repository. Follow these steps once per machine. No prior VS Code, Python, or GitHub setup is assumed.

## 1. Accounts and access

- [ ] Create a personal GitHub account at [github.com](https://github.com/) if you do not already have one.
- [ ] Ask the project owner to add your GitHub account to the `APEHamiltonCompany` organization and grant access to the relevant repository. You do **not** need to create an organization.
- [ ] Accept the organization/repository invitation from GitHub, if one is sent.

## 2. Recommended folder structure

Keep all repositories under `C:\repos`, so every repository is a direct subfolder of it — for example `C:\repos\<project-name>`.

- [ ] Create the folder `C:\repos` if it does not already exist. Avoid spaces in repository paths.

## 3. Install the required software

### Visual Studio Code

- [ ] Download and install [Visual Studio Code](https://code.visualstudio.com/).
- [ ] In VS Code, install the Microsoft **Python** extension. If prompted, also install the **Python Debugger** extension.
- [ ] Download and install [Git for Windows](https://git-scm.com/download/win). The default installation options are fine. After installing, open a new terminal and check that it is available:

  ```powershell
  git --version
  ```

  VS Code uses this Git installation for its built-in Source Control features.

### Python

- [ ] Install Python **3.12.10** for Windows. The current development setup used the Microsoft Store version.
- [ ] Open a new terminal (or restart VS Code) and check that Python is available:

  ```powershell
  python --version
  ```

  The output should identify Python 3.12.10. If `python` opens the Microsoft Store rather than running Python, check **Settings > Apps > Advanced app settings > App execution aliases** and ensure the Python aliases are enabled, then open a new terminal and try again.
- [ ] Check that pip is available through Python:

  ```powershell
  python -m pip --version
  ```

  Use `python -m pip` rather than a bare `pip` command to ensure packages are installed for the Python interpreter you intend to use.

### GitHub Desktop

- [ ] Download and install [GitHub Desktop](https://desktop.github.com/).
- [ ] Sign in with your personal GitHub account.
- [ ] Use **File > Clone repository** to clone the project you were added to. Select the repository under `APEHamiltonCompany` and choose `C:\repos` as the parent folder.

> GitHub Desktop works alongside the Git for Windows installation: VS Code's Source Control features use Git for Windows, while GitHub Desktop handles sign-in and cloning.

## 4. Open the project

- [ ] In GitHub Desktop, choose **Repository > Open in Visual Studio Code**, or open the cloned project folder from VS Code using **File > Open Folder**.
- [ ] In VS Code, open a terminal with **Terminal > New Terminal**. Confirm that the terminal is at the project root (the folder containing the project's README).

## 5. Create and use a project virtual environment

Create a virtual environment in the project folder so project packages do not get installed globally or mixed with other projects.

In the VS Code PowerShell terminal at the project root, run:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
```

If PowerShell blocks activation because of the execution policy, use **Command Prompt** as the VS Code terminal and activate with:

```cmd
.venv\Scripts\activate.bat
```

Activation is only needed once per new terminal session. To reactivate later, run the appropriate activation command above.

## 6. Install project packages

Once the virtual environment is activated, install the packages the project needs. If the project ships a `requirements.txt`, use:

```powershell
python -m pip install -r requirements.txt
```

Otherwise install the named packages directly, for example:

```powershell
python -m pip install <package1> <package2>
```

## 7. Select the project Python interpreter in VS Code

- [ ] Open the Command Palette with **Ctrl+Shift+P**.
- [ ] Run **Python: Select Interpreter**.
- [ ] Select the interpreter in the project `.venv` folder (usually shown as `.venv\Scripts\python.exe`).

This makes VS Code run and debug the project using its virtual environment.

## Notes

- The virtual environment contains locally installed files and must not be committed. The repository `.gitignore` should include `.venv/`, `__pycache__/` and `*.py[cod]`.
