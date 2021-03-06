# Botrix

![Botrix](https://cdn.discordapp.com/attachments/747602999035166810/757838697080160356/logo_wo_background.png)

An Opensource discord bot list developed by [Windows](https://github.com/WindowsCmd), [Awish](https://github.com/Awish-Senpai), Mei-chan, [Toxic-dev](https://github.com/TheRealToxicDev), [PixelSized](https://github.com/PixelSized), [Dylan James](https://github.com/dylanjamesdev) to hopefully replace [this](https://github.com/Sank6/Discord-Bot-List). If you want to contribute open a pull request and the development team will take a look! For support join our [support server](https://discord.gg/RJsJYgMuRd)

# Features

- Clean and modern UI
![Botrix Clean and Modern UI](https://i.imgur.com/AK1cTYv.png)

- Bot awards plus currency system (Setup for paypal)
![Botrix Award System](https://i.imgur.com/1fqoGsm.png)

- Server listing (beta)
![Botrix Server Listing](https://i.imgur.com/OyFsH6d.png)

- Bot banners
![Botrix Bot Banner](https://i.imgur.com/hgTJhGi.png)

- Certified bot program
![Botrix Bot Certification Program](https://i.imgur.com/xYmHg6k.png)

- Easy-to-use Admin Panel
![Botrix Admin Panel](https://i.imgur.com/RazPeYV.png)

- Stylish 404 Page
![Botrix 404 Page](https://i.imgur.com/PcfjLGA.png)

- Personal CDN

# Prerequisites

Ensure you have the following installed before running botrix

- [Node.js](https://nodejs.org/en/) V12 or up
- npm version 3 or up

# Installation

To start and host your own instance of botrix follow these instructions!

```
$ git clone https://github.com/botrixlist/botrix
$ npm i
```

# Basic Setup

Once you clone the repo into a folder, open config.json in your text editor of choice.
First off lets configure authentication set the `id` property to your client id, and `clientSecret` to your client secret.
To configure the callback go into your discord developer portal and add an oauth2 redirect to `yourwebsite.com/api/callback` then go back to the config file and replace `domain` with your base domain example: `"https://botrix.cc"`. For completly free hosting you can [create a free database with mongodb atlas](https://www.mongodb.com/try). Once you have the connection string replace `MongoDbServer` with your connection string. Replace `Token` with your bot token and `ServerToken` with your server bot token. I would recomend you keep the defualt port as long as your are not running on localhost. In the field `AppId` put in your client id and `callback` as the same thing as you put when you setup your oauth2 redirects.
The next thing we will configure is the owner users, these users will have acsess to the eval command and the website admin panel and verifacation to bots in the `OWNER_USERS` field put the discord ids of the owners. Next will be the admin users, these users will have acsess to the admin panel, and to verify bots. This permission role is for the verifiers, in `ADMIN_USERS` put the discord ids of your verifiers. Next we will setup default member and bot roles. Create a new role called Unverifed bots, copy the id of that role and paste it into this field `UNVERIFIED_ROLE`. Next create a role called members copy the id and then paste it in `BOT_DEVELOPER_ROLE_ID`. Now we can setup the verified bot developer, and bot roles. Create a new role called Verified Developer, copy the id and paste it into `BOT_DEVELOPER_ROLE_ID_VERIFIED`. Create another role called Verified bots and paste the id of that role into `VERIFIED_ROLE`. Paste your guild id into `GUILD_ID`. Don't worry! We are almost done, these next params are for the website logs `greeting_chan` is the greeting channel id, `leave_chan` is for leave logs, and `logging_chan` and `MOD_LOG` is for all website logs (Updated bot pages, added bots, verified bots.),`VOTE_LOG` is for logging votes,`CERT_LOGS` are for all pending and new certifacation requests. Now for the hard part! Go into `/src/veiws/add.ejs` and change line 292* `fetch('https://cdn.botrix.cc/uploadBanner', {` to fetch your file uploading server see below how to set up your own file hosting server. Next go to line 297* 298\* and change the `https://cdn.botrix.cc/` to your image uploading server, please keep the /banner/ to keep compatibility. Do the same on the file `/src/views/edit.ejs` on line 181\* 186\* and 188\*. Congradulations! You have setup an instance of botrix!

## Serving files for banners (CDN)

This part of the guide will showcase on how to setup an image hosting service to upload banners on, for this you **will** need a vps. In the root dir of botrix go to botrix-fielupload
in config.json setup the cdn url to your vps's ip or a subdomain pointing to the vps. Finally run it on the vps and your cdn network will be up.
