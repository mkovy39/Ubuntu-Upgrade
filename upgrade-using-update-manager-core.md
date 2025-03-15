## Upgrade Using `update-manager-core`

### 1️⃣ Update Current Packages
```bash
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
```
**Explanation:**
- `apt update` → Refreshes package lists.
- `apt upgrade` → Upgrades installed packages.
- `apt full-upgrade` → Resolves dependencies and removes unnecessary packages.

### 2️⃣ Install `update-manager-core`
```bash
sudo apt install update-manager-core
```
**Ensures the necessary upgrade tools are installed.**

### 3️⃣ Check Upgrade Configuration
```bash
cat /etc/update-manager/release-upgrades
```
Ensure the file contains:
```
Prompt=lts
```
If not, edit the file:
```bash
sudo nano /etc/update-manager/release-upgrades
```
Change `Prompt=never` or `Prompt=normal` to `Prompt=lts`, then **save and exit** (`CTRL + X`, then `Y`, then `Enter`).

### 4️⃣ Start the Upgrade Process
```bash
sudo do-release-upgrade -d
```
**Explanation:**
- `do-release-upgrade` → Starts the Ubuntu upgrade.
- `-d` → Allows upgrades to a new development release **(if stable release is unavailable)**.

For **stable releases**, run:
```bash
sudo do-release-upgrade
```

### 5️⃣ Follow On-Screen Instructions
- Press `Y` when prompted.
- If asked about config files, choose **“keep existing”** unless you want defaults.

### 6️⃣ Reboot the System
```bash
sudo reboot
```

### 7️⃣ Verify the Upgrade
```bash
lsb_release -a
```
Expected output:
```
Ubuntu 24.04 LTS
```

### 8️⃣ Check Kernel Version (Optional)
```bash
uname -r
```

## ✅ Upgrade Complete!
You have successfully upgraded to **Ubuntu 24.04 LTS** 🎉.
