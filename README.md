# CMDLookup

A smart Linux command lookup and package manager wrapper tool. It checks your local system for utilities, fetches detailed syntax/usage guides from ```cheat.sh```, and matches the exact upstream package names across multiple package managers using ```command-not-found.com```.

---

## Installation

### Debian / Ubuntu / Mint / Zorin
Add the repository and install natively via `apt`:

```bash
curl -1sLf '[https://dl.cloudsmith.io/public/pixeleyesd/cmdlookup/setup.deb.sh](https://dl.cloudsmith.io/public/pixeleyesd/cmdlookup/setup.deb.sh)' | sudo -E bash
sudo apt install cmdlookup
```

Note for Downstream Distros (e.g., Zorin OS): If the setup script fails to detect your specific release, force it to use the upstream Ubuntu base by running:

```bash
curl -1sLf '[https://dl.cloudsmith.io/public/pixeleyesd/cmdlookup/setup.deb.sh](https://dl.cloudsmith.io/public/pixeleyesd/cmdlookup/setup.deb.sh)' | distro=ubuntu version=24.04 codename=noble sudo -E bash
sudo apt install cmdlookup
```

### RedHat / Fedora / CentOS
Add the repository and install natively via dnf:

```bash
curl -1sLf '[https://dl.cloudsmith.io/public/pixeleyesd/cmdlookup/setup.rpm.sh](https://dl.cloudsmith.io/public/pixeleyesd/cmdlookup/setup.rpm.sh)' | sudo -E bash   
sudo dnf install cmdlookup
```
## Usage
Simply run cmdlookup followed by the command or binary name you want to explore:

```bash
cmdlookup [command] [options]
```

## Examples
### Basic Lookup
To look up an uninstalled or unfamiliar command (like nvim):

```bash
cmdlookup nvim
```

This will display:

Whether it is installed locally (and its path).

A clear, human-readable description.

The exact installation strings for APT, Pacman, DNF, Zypper, Homebrew, and Snap (properly mapped so you don't install the wrong package names).

An Explanation and Commands syntax guide.

### Filtering by Package Manager
If you only care about a specific ecosystem, use a filter flag to keep your terminal output focused:

```bash
cmdlookup nvim --apt
cmdlookup nvim --pacman
cmdlookup nvim --dnf
cmdlookup nvim --zypper
cmdlookup nvim --brew
cmdlookup nvim --snap
```

| Flag     | Long Flag     | Description |
|:---------|:----------|:------------|
| ```-i```   | ```--install```    | Automatically runs your system's native package manager command to install the targeted tool. |
| ```-v``` | ```--verbose``` | Shows real-time network connections and API fallback status. |
| ```-u``` | ```--update``` | Prints the manual command strings needed to sync your local package databases. |
|  | ```--json``` | Outputs the command's local presence status and short description as a structured JSON object (perfect for script scripting/piping). |
| ```-h``` | ```--help``` | Displays the help menu. |

### Script Piping with JSON
You can seamlessly integrate ```cmdlookup``` into other automation workflows:

```bash
cmdlookup nano --json
# Outputs: {"command": "nano", "status": "Installed at /usr/bin/nano", "description": "small and friendly text editor"}
```
