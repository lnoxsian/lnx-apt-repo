# lnx APT Repository

A personal Debian/Ubuntu package repository hosting custom packages and applications.

## About

This repository provides signed Debian packages for easy installation on systems running Debian or Ubuntu-based distributions. All packages are cryptographically signed for security and integrity verification.

## Installation

### Quick Start

To add this repository to your system and start installing packages, follow these three steps.

#### Step 1 — Download the public key

```bash
curl -fsSL https://lnoxsian.github.io/lnx-apt-repo/pubkey.gpg | sudo gpg --dearmor -o /usr/share/keyrings/lnx-apt-repo-keyring.gpg
```

#### Step 2 — Add the repository to your sources list (arch=amd64)

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/lnx-apt-repo-keyring.gpg] https://lnoxsian.github.io/lnx-apt-repo any main" | sudo tee /etc/apt/sources.list.d/lnx-apt-repo.list > /dev/null
```

#### Step 3 — Update your package cache and install packages

```bash
sudo apt update
sudo apt install <package-name>
```

### Step-by-Step Explanation

#### Step 1: Install the Repository Key

The repository uses GPG signatures to ensure package authenticity. Download the public key:

```bash
curl -fsSL https://lnoxsian.github.io/lnx-apt-repo/pubkey.gpg | sudo gpg --dearmor -o /usr/share/keyrings/lnx-apt-repo-keyring.gpg
```

This command:
- Fetches the public key from the repository
- Converts it from ASCII format to binary format (`--dearmor`)
- Saves it to the system keyring directory

#### Step 2: Add Repository to Sources

Add the repository to your APT sources list:

```bash
echo "deb [signed-by=/usr/share/keyrings/lnx-apt-repo-keyring.gpg] https://lnoxsian.github.io/apt-repo any main" | sudo tee /etc/apt/sources.list.d/lnx-apt-repo.list > /dev/null
```

This configuration:
- Points APT to the repository URL
- Specifies the GPG key for signature verification
- Uses `any` as the distribution (works across Debian/Ubuntu versions)
- Uses `main` as the component

#### Step 3: Update Package Cache

Refresh your package cache to fetch the latest package information:

```bash
sudo apt update
```

#### Step 4: Install Packages

Now you can install packages from this repository:

```bash
sudo apt install whatsapp
```

## Security

- All packages in this repository are signed with a GPG key
- Package signatures are verified before installation
- The public key is distributed securely via HTTPS

## Removing the Repository

To remove this repository from your system:

```bash
sudo rm /etc/apt/sources.list.d/lnx-apt-repo.list
sudo apt update
```

## Troubleshooting

### GPG Key Not Found
If you encounter signature verification errors, ensure the public key was installed correctly:

```bash
gpg --list-keys
```

### Repository Not Found
Verify the sources list file was created:

```bash
cat /etc/apt/sources.list.d/lnx-apt-repo.list
```

### Package Not Found After Update
Make sure to run `sudo apt update` after adding the repository.

## Support

For issues or questions, please refer to the repository's issue tracker or documentation.