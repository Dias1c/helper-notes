# WSL - Windows Subsystem Linux
What the [WSL](https://docs.microsoft.com/ru-ru/windows/wsl/about)?
## Routes
### How to:
- [Install WSL?](How-to-install-WSL?)
- [Update Linux?](How-to-update-Linux?)
- [Reset password on WSL?](How-to-reset-password-on-WSL?)
- [Turn off Linux on Windows?](How-to-turn-off-Linux-on-Windows?)

## How to install WSL?
> Official instruction of installation wsl 2 [here](https://docs.microsoft.com/ru-ru/windows/wsl/install-manual)


## How to update Linux?

### Step 1. Download update
```bash
sudo apt update
```

### Step 2. Install update
```bash
sudo apt -y update
```

## How to reset password on WSL?
- `{user_name}` - your user name on Linux

#### If your disto is:
- Ubuntu: `ubuntu config --default-user root`
- openSUSE Leap 42: `openSUSE-42 config --default-user root`
- SUSE Linux: `SLES-12 config --default-user root`
- Debian: `debian config --default-user root`
- Kali Linux: `kali config --default-user root`

### Step 1. Change default user for WSL
```powershell
# Here is we change default user as root
ubuntu config --defaul-user root
# After this command you will be on bash as root
ubuntu
# check who are you. You must be `root`
whaomi
```

### Step 2. Reset password on WSL user
After first step go into WSL
```bash
# Reset your password. And set your password
passwd {user_name}
# Leave from Ubuntu
exit
```

### Step 3. Reset default user
```powershell
ubuntu config --defaul-user {user_name}
```


## How to turn off Linux on Windows?
Just run this command on `powershell`
```powershell
# This command turn off procces WSL on Windows
wsl --shutdown
```