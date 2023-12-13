# MySQL on Arch


## Update Package List
 ```zsh
 sudo pacman -Syu
 ```

## Install mariaB
```zsh
sudo macman -S mariadb
```

## Start mariadb
```zsh
sudo systemctl start mariadb
```

## Enable mariadb
```zsh
sudo systemctl enable mariadb
```

## Stop mariadb
```zsh
sudo systemctl stop mariadb
```

## Check status
```zsh
sudo systemctl status mariadb
```
                
## Secure mariadb installation
```zsh
sudo mysql_secure_installation
```

## Additional Resources:

ArchWiki MariaDB Page: https://wiki.archlinux.org/

Official MariaDB Documentation: https://mariadb.org/documentation/



