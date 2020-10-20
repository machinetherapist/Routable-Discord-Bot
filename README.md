# Routable-Discord-Bot
discord bots a different perspective.


as I was trying to improve my whitelist script tonight, there was a deficiency in eye discord.js 
and I wanted to approach the issue differently.
The base I bought was the routing 
structure of the web servers and I simply 
wrote a routable discord.js module. 
This means that you can build discord bot just by typing the route (object).


```js
const goat = require('./goatbot.js')
const token = 'BOT TOKEN'

var bot = new Monitor(token)

var routes = [
  {
    state: 1,
    prefix: "add",
    action: function(steamId, discordId, req) {
      console.log(steamId, discordId);
    }
  },
  {
    state: 1,
    prefix: "remove",
    action: function(steamId, discordId, req) {
      console.log(steamId, discordId);
      req.reply(steamId)
    }
  }
 
]

bot.init(routes)

bot.client.on('ready', () => {
  console.log(`Monitor started as ${bot.client.user.tag}!`);
});

bot.client.on('message', msg => {
  var msgString = msg.toString()
  if (msgString.includes("!prefix")) bot.learnRequest(msg), bot.solveRequest()
}); 
```
