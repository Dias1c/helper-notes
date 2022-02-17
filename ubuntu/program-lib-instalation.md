# How Install Programs or Libraries
Recomend to install to opt

## command sudo
Fist Check version
```
sudo apt-cache show {app}
```
if version is what you want, just run
```
sudo apt install {app}
```

## .tar
Your programs should be in installed in folder "/opt"
- Example:
```
# First You should downlad using wget or something else
wget "downlad-link"

# Unpack tar file
## If .tar.gz
sudo tar -xzf {app.tar.gz}
## If .tar.xz
sudo tar -xf {app.tar.xz}

# After Remove tar file
rm {app.tar.gz}
```

### if program
```
# Move upacked program|folder to opt with his name
sudo mv {app} /opt/{app}
# Create link in bin folder
sudo ln -s /opt/{app}/{app}/bin /usr/bin/{app}
```

### if library
```
# Move upacked program|folder to opt with his name
sudo mv {app} /usr/local/lib/{app}
# Create link in bin folder
# Add to .profile if you want
cd && nano .profile
# Add extends
```

## .deb
- Example:
```
# Install
sudo dpkg -i {app.deb}
```

## Postman
### How to install?
```
# First Downlad it
sudo tar -xzf Postman-linux-x64-6.2.4.tar.gz
rm Postman-linux-x64-6.2.4.tar.gz
sudo mv Postman /opt/Postman
sudo ln -s /opt/Postman/Postman /usr/bin/postman
```
