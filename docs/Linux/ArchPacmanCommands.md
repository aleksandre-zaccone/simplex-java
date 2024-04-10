# **Arch Pacman Commands**

Arch's pacman is a powerful package manager used to install, remove, upgrade, and manage software on your system. 
This tutorial will guide you through understanding pacman's syntax, common flags, and optional flags with examples.

<br>

# **Pacman Syntax Breakdown**

The basic syntax for a pacman command follows this structure:
```zsh
pacman <flag> [options] <package_name(s)>
```

- **pacman**: This is the command itself flag: This tells pacman what action to take.

- **Common flags include:**
    - **S**: Install packages (including dependencies)
    - **R**: Remove packages
    - **Q**: Query package information
- **options:** These are optional flags that modify the behavior of the main flag.
    - **s**: Search for a package in the repositories (local and remote), do not install
      - **u**: Upgrade all out-of-date packages
      - **y**: Refresh package databases
- **package_name(s):** This specifies the name(s) of the package(s) you want to interact with. You can provide multiple package names separated by spaces.

<br>

# **Most commonly used Pacman commands in Arch Linux with examples**

1. **Updating the package database and upgrading all packages**:
   ```zsh
   sudo pacman -Syu
   ```
   This command synchronizes the local package database with the remote repositories and then upgrades all installed packages to their latest versions. 

2. **Installing a package**:
   ```zsh
   sudo pacman -S <package_name>
   ```
   This command installs the specified package and its dependencies.

3. **Removing a package**:
   ```zsh
   sudo pacman -R <package_name>
   ```
   This command removes the specified package from the system.

4. **Searching for a package**:
   ```zsh
   pacman -Ss <search_term>
   ```
   This command searches the package databases for packages matching the given search term.

5. **Listing installed packages**:
   ```zsh
   pacman -Q
   ```
   This command lists all the packages currently installed on the system.

6. **Listing explicitly installed packages**:
   ```zsh
   pacman -Qe
   ```
   This command lists the packages that were explicitly installed by the user, as opposed to those installed as dependencies.

7. **Listing orphaned dependencies**:
   ```zsh
   pacman -Qdt
   ```
   This command lists the packages that are no longer required by any other package and can be safely removed.

8. **Removing orphaned dependencies**:
   ```zsh
   sudo pacman -Rns $(pacman -Qdtq)
   ```
   This command removes all the orphaned dependencies from the system.

9. **Displaying package information**:
   ```zsh
   pacman -Qi <package_name>
   ```
   This command displays detailed information about the specified package.

10. **Listing files owned by a package**:
    ```zsh
    pacman -Ql <package_name>
    ```
    This command lists all the files that are owned by the specified package.


