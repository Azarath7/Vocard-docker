<a href="https://discord.gg/wRCgB7vBQv">
    <img src="https://img.shields.io/discord/811542332678996008?color=7289DA&label=Support&logo=discord&style=for-the-badge" alt="Discord">
</a>

# Vocard (Discord Music Bot)
> Vocard is a simple custom Disocrd Music Bot built with Python & [discord.py](https://discordpy.readthedocs.io/en/stable/) <br>
Demo: [Discord Bot Demo](https://discord.com/api/oauth2/authorize?client_id=890399639008866355&permissions=36708608&scope=bot%20applications.commands),
[Dashboard Demo](https://vocard.xyz)

# Host for you?
<a href="https://www.patreon.com/Vocard">
    <img src="https://img.shields.io/endpoint.svg?url=https%3A%2F%2Fshieldsio-patreon.vercel.app%2Fapi%3Fusername%3Dendel%26type%3Dpatrons&style=for-the-badge" alt="Patreon">
</a>

# Table Of Contents

1. [Introduction](#Vocard (Discord Music Bot))
2. [Previews](#previews)
    - [Discord Bot](#discord-bot)
    - [Dashboard](#dashboard)
3. [How to Install Vocard using Docker](#how-to-install-vocard-using-docker)
    - [Download the necessary files](#download-the-necessary-files)
    - [Configure Docker Compose](#configure-docker-compose)
    - [Configure `settings.json` (optional)](#configure-settingsjson-optional)
    - [Installation Steps](#installation-steps)
    - [Troubleshooting](#troubleshooting)

---

## Previews
#### Discord Bot
| | |
|:-------------------------:|:-------------------------:|
|<img src="https://user-images.githubusercontent.com/94597336/227766331-dfa7d360-18d7-4014-ac6a-4fca55907d99.png" width="450">    |This bot can be deeply customised.<br> You can change media buttons,<br> player layout, player text and etc.<br><br><br><img src="https://user-images.githubusercontent.com/94597336/227766379-c824512e-a6f7-4ca5-9342-cc8e78d52491.png" width="450">|
|<img src="https://user-images.githubusercontent.com/94597336/227766408-37d733f7-c849-4cbd-9e17-0cd5800affb3.png" width="450">    |<img src="https://user-images.githubusercontent.com/94597336/227766416-22ae3d91-40d9-44c0-bde1-9d40bd54c3af.png" width="450">|

#### Dashboard
<img src="https://github.com/ChocoMeow/Vocard/assets/94597336/53f31f9f-57c5-452c-8317-114125ddbf03">
<img src="https://github.com/ChocoMeow/Vocard/assets/94597336/b2acd87a-e910-4247-8d5a-418f3782f63f">

---
 
# How to Install Vocard using Docker

## Download the necessary files:
    docker-compose.yml
    application.yml
    settings.json
Place these files on your host machine.
        
 Should look like this:
```
### This folder will be your bot's configuration and log file directory.
    /path/to/your/directory/
    ├── docker-compose.yml
    ├── application.yml
    ├── settings.json
    └── logs/
        └── supervisor/
```
`Ensure the /logs/supervisor/ folder is created within your chosen directory.`

## Configure Docker Compose:

Edit `docker-compose.yml` and fill in the required [environment](Environments) values. These values are crucial for the bot to work.
If you're going to use `web-dashboard` - uncomment `ports` directive for vocard in `docker-compose.yml

``` yaml
networks:
            - vocardbot
        ## Uncomment if you're going to use web dashboard.
        ports:
            - 37123:37123
```

### Environments
| Values | Description |
| --- | --- |
| TOKEN | Your Discord bot token [(Discord Portal)](https://discord.com/developers/applications) |
| CLIENT_ID | Your Discord bot client id [(Discord Portal)](https://discord.com/developers/applications) |
| CLIENT_SECRET_ID | Your Discord bot client secret id [(Discord Portal)](https://discord.com/developers/applications) ***(optional)*** |
| SERCET_KEY | Secret key for dashboard ***(optional)*** |
| BUG_REPORT_CHANNEL_ID | All the error messages will send to this text channel ***(optional)*** |
| SPOTIFY_CLIENT_ID | Your Spoity client id [(Spotify Portal)](https://developer.spotify.com/dashboard/applications) ***(optional)*** |
| SPOTIFY_CLIENT_SECRET | Your Spoity client sercret id [(Spotify Portal)](https://developer.spotify.com/dashboard/applications) ***(optional)*** |
| GENIUS_TOKEN | Your genius api key [(Genius Lyrics API)](https://genius.com/api-clients) ***(optional)*** |
| MONGODB_URL | Your Mongo datebase url [(Mongodb)](https://www.mongodb.com/) |
| MONGODB_NAME | The datebase name that you created on [Mongodb](https://www.mongodb.com/) |
| REDIRECT_URI | Redirect uri that you've specified on [Discord Developer Portal](https://discord.com/developers/applications) (optional only for non-dashboard build)|

---

### Configure `settings.json` (optional)

#### Stock values are good to go, but if you want to customize your Vocard here is `settings.json` breakdown:
* For `nodes` you have to provide host, port, password and identifier of the [Lavalink Server](https://github.com/freyacodes/Lavalink)
* For `prefix` you can set the prefix of the bot. (If you don't provide any prefix, the bot will disable the message command).
* For `activity` you can set the activity of the bot. [Example Here](https://github.com/ChocoMeow/Vocard/blob/main/PLACEHOLDERS.md#bot-activity-activity-are-updated-every-10-minutes)
* For `bot_access_user` you can pass the [discord user id](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-). Example: `[123456789012345678]`
* For `embed_color` you must pass a [Hexadecimal color code](https://htmlcolorcodes.com/) and add `0x` before the color code. Example: `"0xb3b3b3"`
* For `default_max_queue` you can set a default maximum number of tracks that can be added to the queue.
* For `lyrics_platform` you can set lyrics search engine (e.g. `A_ZLyrics`, `Genius`, `lyrist`)<br>**NOTE: If you are using Genius as your lyrics search engine, you must install the lyricsgenius module (`pip install lyricsgenius`)**
* For `ipc_server` you can set the host, password and enable of the ipc server.
* For `emoji_source_raw` you can change the source emoji of the track with discord emoji like `<:EMOJI_NAME:EMOJI_ID>`
* For `cooldowns` you can set a custom cooldown in the command. Example: `"command_name": [The total number of tokens available, The length of the cooldown period in seconds]`
* For `aliases` you can set custom aliases in the command. Example: `"command_name": [alias1, alias2, ...]`
* For `default_controller` you can set custom embeds and buttons in controller, [Example Here](https://github.com/ChocoMeow/Vocard/blob/main/PLACEHOLDERS.md#controller-embeds)


## Installation Steps:

Open a terminal or SSH session on your host machine.
Navigate to the directory where you saved the configuration files:

`cd /path/to/your/directory/`

Start the Docker containers in detached mode:


`docker-compose up -d`

Installation usually takes just a few minutes. 

---

## Troubleshooting:

### Vocard no connection to node:

Note: Sometimes, the Vocard container might start before its dependencies (like Lavalink). If this occurs, manually restart the Vocard container - it should solve the issue

`docker-compose restart vocard`
    
If encountering issues, ensure ports specified in your docker-compose.yml are not already in use by other services.
In your config directory check log files from /logs/...


```
#### Check the current version
python update.py -c

#### Install the latest version
python update.py -l

#### Install the specified version
python update.py -v VERSION

#### Install the beta version
python update.py -b
```
