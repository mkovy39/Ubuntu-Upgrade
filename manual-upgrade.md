# Upgrade from Ubuntu 18.04 to 22.04 LTS



## Check Current Ubuntu Version
Check the current version of Ubuntu installed on the system.
```sh
cat /etc/os-release
```

## Upgrade to Ubuntu 20.04 (Focal)

### Update APT Sources
Modify the APT sources list to replace `bionic` (Ubuntu 18.04) with `focal` (Ubuntu 20.04).
```sh
cd /etc/apt
cp sources.list sources.list~bkp  # Backup the original sources list
sed 's/bionic/focal/g' sources.list~bkp > sources.list  # Update the release version
```

### Upgrade System (20-30 min)
Update the package lists and upgrade all installed packages.
```sh
apt update  # Fetch updated package lists
apt upgrade # Perform package upgrades
apt dist-upgrade # Handle additional dependencies and conflicts
```
Press **YES** where required.

**Choose version 3.0 (avoid version 4.0 due to package dependency issues).**

### Update SSL Library
Download and install an updated SSL library to avoid compatibility issues.
```sh
wget http://security.ubuntu.com/ubuntu/pool/main/o/openssl1.0/libssl1.0.0_1.0.2n-1ubuntu5.13_amd64.deb
dpkg -i libssl1.0.0_1.0.2n-1ubuntu5.13_amd64.deb
```

### Reboot Server
Reboot the system to apply changes and verify that all services are running correctly.
```sh
reboot
```

---

## Upgrade to Ubuntu 22.04 (Jammy)

### Update APT Sources
Modify the APT sources list to replace `focal` (Ubuntu 20.04) with `jammy` (Ubuntu 22.04).
```sh
cd /etc/apt
rm -rf sources.list~bkp  # Remove previous backup
cp sources.list sources.list~bkp  # Create a new backup
sed 's/bionic/jammy/g' sources.list~bkp > sources.list  # Ensure any residual bionic entries are updated
cp sources.list sources.list~bkp2
sed 's/focal/jammy/g' sources.list~bkp2 > sources.list  # Ensure all focal entries are updated
```

### Upgrade System (20-30 min)
Update the package lists and upgrade all installed packages.
```sh
apt update  # Fetch updated package lists
apt upgrade # Perform package upgrades
apt dist-upgrade # Handle additional dependencies and conflicts
```
Press **ENTER (N)** where required.


### Reboot Server
Reboot the system to apply changes and verify that all services are running correctly.
```sh
reboot
```

After reboot, verify the system.
