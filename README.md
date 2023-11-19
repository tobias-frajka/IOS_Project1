## Introduction
The "mole" (Makes One’s Life Easier) script is a covert tool developed for the Czech counterintelligence agency FDTO (Fakt Děsně Tajná Organizace) to identify a mole within the organization. It functions as a wrapper for text editors, secretly logging and reporting information about document access and modifications. While presented as a tool for increasing efficiency in handling electronic documents, its primary function is to discreetly monitor file activities.

## Features
- **Wrapper for Text Editors:** Operates as a wrapper over text editors, enabling standard editing functions while secretly logging activities.
- **Automatic File Selection:** Chooses the most recently or frequently modified file in a given directory.
- **File Grouping:** Allows assigning files to groups for easier management and filtering.
- **Discreet Operation:** Implements security measures covertly to avoid alerting the mole.
- **Logging and Reporting:** Secretly logs file access and modifications, storing data in a compressed format for analysis.

## Usage
```shell
mole -h
mole [-g GROUP] FILE
mole [-m] [FILTERS] [DIRECTORY]
mole list [FILTERS] [DIRECTORY]
mole secret-log [-b DATE] [-a DATE] [DIRECTORY1 [DIRECTORY2 [...]]]
```

- `-h`: Displays help information.
- `[-g GROUP] FILE`: Opens the specified file, optionally assigning it to a GROUP.
- `[-m] [FILTERS] [DIRECTORY]`: Selects a file from a directory based on various filters, including most frequently or recently modified files.
- `list [FILTERS] [DIRECTORY]`: Lists files edited via the script, applying specified filters.
- `secret-log`: Generates a secret log of file activities, applying date and directory filters.

## Installation
Set the `MOLE_RC` environment variable to specify the location of the log file. The script uses the `EDITOR` environment variable to determine which text editor to use, defaulting to `vi` if not set.

Example:
```bash
export MOLE_RC=$HOME/.config/molerc
export EDITOR=nano
```

## Examples
### Editing Files 
```shell
mole ~/.ssh/config
mole -g bash ~/.bashrc
mole -m ~/documents
```

### Listing Edited Files
```shell
mole list ~/projects
mole list -g bash,git ~/projects
```

### Creating Secret Log
```shell
mole secret-log -a 2023-01-01 -b 2023-01-31 ~/projects
```

## Notes
- The script assumes file and group names do not contain semicolons or colons.
- File operations performed outside the script are not logged.
- Temporary files are not used, except indirectly by other commands (e.g., sed -i).



Project for IOS (Operating systems), 2023, VUT FIT.