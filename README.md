# 🎮 TV Launcher for Ubuntu/Debian HTPC

Forked from [Darkvinx88/TvLauncher](https://github.com/Darkvinx88/TvLauncher)

My edits:
- pywin32 requirement removed from requirements.txt
- linear carousel (for <5 apps) centred on screen

## Installation
```
git clone https://github.com/lizzol/TvLauncher.git
cd TvLauncher

# Install dependencies
sudo apt update
sudo apt install python3-pyqt6 python3-pip

# Then install Python packages
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# And launch
python3 ~/TvLauncher/TvLauncher_Linux.py
```

### Enable autostart
Edit the TVLauncher.desktop file to contain the relevant file paths. Then move to autostart directory:
```
mkdir -p ~/.config/autostart
mv TVLauncher.desktop ~/.config/autostart/
# make executable
chmod +x ~/.config/autostart/TVLauncher.desktop
```

### Run web apps e.g. Jellyfin
Create an executable script to launch in chromium
```
mkdir ~/TvLauncher/apps
nano ~/TvLauncher/apps/launch_Jellyfin.sh # copy in the code block below, save and exit
chmod +x ~/TvLauncher/apps/launch_Jellyfin.sh
```
launch_Jellyfin.sh:
```
#!/bin/bash
chromium --app=http://<your server IP address>:8096/web/#/home --kiosk
```
Then initiate the launcher with `python3 ~/TvLauncher/TvLauncher_Linux.py`, click the `+` and select `~/TvLauncher/apps/launch_Jellyfin.sh` as the executable
