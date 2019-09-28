# Telegram Server Monitor

Monitoring service writen in Python3 to be hosted on your own server.

## Installation
**Talk to @BotFather on Telegram**
- Type `/start` to start a conversation with the bot father.
- Type `/newbot` and follow the instructions to create our own bot.
- Remember the access token - you will need it later.
- You may configure your bot by setting a name or picture.

**Configure your linux server**

```sh
# Create a special user for the bot
sudo adduser telegram --gecos "" --disabled-password

# Install required packages with the package manager
sudo apt install python3-psutil python3-requests python3-netifaces

# OR install Python 3 and dependecies with pip
# use this only if you have problems with the commandline above...
#sudo apt install python3 python3-pip
#sudo python3 -m pip install requests psutil netifaces --upgrade
```

**Download and install Telegram Server Monitor**

```sh
# Change to the created user
su telegram
cd ~

git clone https://github.com/Zeik0s/telegram-server-monitor.git
cd telegram-server-monitor
cp config.template.py config.py

# Edit the config file with your favorite editor (add password, etc...)
vim config.py
```

## Usage

To keep your new telegram bot running when you logout you might want to create a Systemd Service. I added an Example (telegram.service). Copy this file to /etc/systemd/system/ .

You can start the program for testing with
```
python3 daemon.py
```

If you plan to leave it running in the Background, do the following:
```
sudo cp telegram-monitoring.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable telegram-monitoring
sudo systemctl start telegram-monitoring

```
