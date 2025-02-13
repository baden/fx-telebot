# Бот

```
python3 -m venv .venv
source .venv/bin/activate
pip install python-telegram-bot==13.6

set BOT_TOKEN=..
```

Виникли проблеми при встановленні на сервері з системою, яку років з 10 не оновлювали.
Виникли проблеми з python.

Ось послідовність, яка допомогла:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
mcedit ~/.bashrc 
# ADD
# export PATH=$PATH:$HOME/.local/bin
. ~/.bashrc 
uv python install 3.10
uv venv --python 3.10
source .venv/bin/activate
uv pip install python-dotenv
uv pip install python-telegram-bot==13.6
export BOT_TOKEN="..."
uv run ./bot.py
```

Виконати

```
sudo ln -s /home/baden/fx-telebot/tbot.service /etc/systemd/system/tbot.service
```


Створити файл .env:
```
BOT_TOKEN=....
```


```bash
sudo systemctl enable tbot
sudo systemctl daemon-reload
sudo systemctl start tbot
sudo systemctl status tbot
```


або варіант для Upstart (Ubuntu 14.04)

```bash
ln -s /home/baden/fx-telebot/fx-telebot.conf /etc/init/fx-telebot.conf
```


```bash
sudo service tbot enable
sudo service tbot restart
sudo service tbot start
sudo service tbot status
```


Самопідписний сертифікат якшо з letsencrypr не вийде

```
openssl req -newkey rsa:2048 -sha256 -nodes -keyout telegram.key -x509 -days 365 -out telegram.pem -subj "/C=US/ST=New York/L=Brooklyn/O=Example Brooklyn Company/CN=fx.navi.cc"
```
