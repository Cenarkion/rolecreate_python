# Ansible Role Creator

This script automates the creation of a new Ansible role. It creates a new directory structure for the role, initializes a git repository, and pushes it to your GitHub account.

## Requirements

- Python 3
- `requests` module (`pip install requests`)
- `ansible` (`pip install ansible`)
- Git

## Installation

1.  Clone this repository or download the `rolecreate` script.
2.  Make sure the script is executable:
    ```bash
    chmod +x rolecreate
    ```
3.  Place the script in a directory that is in your system's `PATH` (e.g., `/usr/local/bin`).

## Usage

```bash
rolecreate -n <new_role_name> [options]
```

### Options

-   `-n`, `--name`: (Required) The name of the new Ansible role.
-   `-p`, `--private`: Create a private GitHub repository.
-   `--repo-path`: The local path where the role directory will be created. Defaults to the current directory.
-   `--github-username`: Your GitHub username. The script will attempt to get this from your git configuration (`user.name`) if not provided.

### GitHub Token Management

The script needs a GitHub personal access token with the `repo` scope to create repositories on your behalf. The token is managed as follows:

1.  **Environment Variable:** The script first checks for the `GITHUB_TOKEN` environment variable. If set, it will use this token.
2.  **Configuration File:** If the environment variable is not set, the script will look for a token in `~/.rolecreate/config.ini`.
3.  **Interactive Prompt:** If the token is not found in either of the above, the script will securely prompt you to enter it. You will then be given the option to save it to `~/.rolecreate/config.ini` for future use. The configuration file will be created with secure permissions (read/write only for the owner).

### Example

```bash
# Create a new public role in the current directory
./rolecreate -n my-ansible-role

# Create a new private role in a specific directory
./rolecreate -n my-secret-role -p --repo-path /tmp/ansible/roles --github-username my-github-user
```

## License

BSD

## Author Information

Jeff Wilkins
(Refactored by Gemini)