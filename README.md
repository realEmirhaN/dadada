# maniacbot
A discord bot for didney worl who has an appetite for non-nutritive substances

## Dependencies
This discord bot uses discord.js, dotenv, googleapis, node-opus, and ytdl-core.  
These dependencies are part of the [package.json](https://github.com/aaronshappell/picabot/blob/master/package.json) and can be installed locally via npm.

## Installation and Running
How to install and run picabot for various systems/hosting options.  
The google api key isn't necessary but is required for the `yt` command to work.
### Locally
First install nodejs and npm. Download them for your system [here](https://nodejs.org/en/download/).  
You can then install the bot by cloning the git repo with `git clone https://github.com/aaronshappell/picabot.git`. Then you must install the necessary dependencies with `npm install` in the project directory. Make sure you have a `.env` file with your bot token and google api key as `BOTTOKEN` and `GOOGLEAPIKEY` respectively. See [example.env](https://github.com/aaronshappell/picabot/blob/master/example.env) for details.  
You can run the bot with `node ./` from within the project directory. It will print `Bot ready` when the bot is ready to recieve commands.
### Heroku
Make sure you have set your config variables in heroku (environment variables) with your bot token and google api key as `BOTTOKEN` and `GOOGLEAPIKEY` respectively. You also need to add a [ffmpeg buildpack](https://github.com/jonathanong/heroku-buildpack-ffmpeg-latest) to your project for voice to work.  
You can run the bot by pushing to your remote heroku repository or on the website. Doing so will automatically install the necessary dependencies for your dyno instance. On the resources tab of your heroku app turn off the web dyno and turn on the worker dyno. You can check the log with `heroku logs --tail` to verify that your bot is running and you will see `Bot ready`.  
**Note:** messages saved with the `save` command will not be permanently saved due to heroku's ephemeral file system and the dyno lifecycle.
### Google Compute Engine
Soon to come...

## Commands
### Current Commands
`m!yardım <command> | -a ve --all`: Kullanabileceğiniz komutların listesini veya belirli komutlar hakkında ayrıntıları verir.
`m!bot`: Bot hakkında bilgi verir.  
`m!ping`: Botun Pingini Gösterir. 
`m!roll <amount>d<sides>+<modifier>`: roll.
`m!8ball`: Bir servet için sihirli bir 8 top ister.
`m!kaydet <key> <message>`: Belirli bir anahtar ile kişiselleştirilmiş bir mesaj kaydeder.
`m!kaydedilenler <key>`: Kayıtlı mesajlarınızı listeler veya verilen bir tuşla kaydedilmiş bir mesajı çağırır.
`m!sil <key>`: Kayıtlı tuşu siler.
`m!yönlendir`: Özel bir hakaret göndermek için botu ses kanalınıza yönlendirin.
`m!linkekle <link>`: YouTube linki ekle .
`m!yt <query>`: YouTube dan kuyruğa müzik ekle  .
`m!play`: Mevcut şarkıyı devam ettirir  .
`m!pause`: Mevcut şarkıyı durdur .
`m!önceki <amount>`: Belirli bir şarkı miktarıyla sıraya geri atlar .
`m!ileri <amount>`: Belirli miktarda şarkı ile sıraya girer  .
`m!atla <index>`: Sıradaki dizine göre belirli bir şarkıya atlar.
`m!rastgele`: Kuyruktaki şarkıları rastgele seçer.  
`m!sil <index>`: Sıradaki şarkı kuyruğunu veya belirli bir şarkıyı temizler  .
`m!kuyruk`: Şarkının kuyruğunu karıştırır  .
`m!otodeğiş`: Şarkı sırasının şarkılarını otomatik olarak değiştirir  .
`m!şarkı`: Şu anda çalınan şarkı hakkında bilgi verir  .
`m!müzik`: Su anda kuyrukta bulunan sarkilarin bir listesini verir. 
### Example Command
A command in the commands object consists of three parts: usage, description, and its process.
```
"command": {
    "usage": "<argument>",
    "description": "Describes what the command does",
    "process": function(message, args){
        //Do stuff here
    }
}
```
