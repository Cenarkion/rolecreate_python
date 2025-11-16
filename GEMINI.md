# Project Overview

This project is a Python script that automates the creation of Ansible roles. It creates a new directory structure for an Ansible role, initializes a git repository, and pushes it to GitHub.

The script uses the following technologies:
- Python 3
- GitHub API v3
- `ansible-galaxy`

## File Descriptions

- `rolecreate`: The main Python script that contains the logic for creating the Ansible role and GitHub repository.
- `secrets.py`: This file is no longer used. The script now uses the `GITHUB_TOKEN` environment variable.
- `README.md`: The original README file for the project.

# Building and Running

## Dependencies

- Python 3
- `requests` module (`pip install requests`)
- `ansible`

## Setup

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd <repository-name>
    ```
2.  **Install dependencies:**
    ```bash
    pip install requests
    ```
3.  **Set `GITHUB_TOKEN` (optional):**
    You can set the `GITHUB_TOKEN` environment variable to your GitHub personal access token. If you don't set it, the script will prompt you to enter it.
    ```bash
    export GITHUB_TOKEN='your_github_token'
    ```

## Running the script

To create a new Ansible role, run the `rolecreate` script with the `-n` or `--name` flag, followed by the name of the role you want to create.

```bash
./rolecreate -n my-new-role
```

You can also specify the following optional arguments:
- `--private` or `-p`: Create a private repository.
- `--repo-path`: The path to the directory where the new role will be created (defaults to the current directory).
- `--github-username`: Your GitHub username (the script will try to get it from your git config `user.name` if not provided).

Example:
```bash
./rolecreate -n my-new-private-role -p --repo-path /tmp/roles --github-username myuser
```

# Development Conventions

The script has been significantly improved from its original version. It now follows better practices for configuration, secret management, and error handling.
