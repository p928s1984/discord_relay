based on the free version of https://www.gmodstore.com/scripts/view/3277/discord-garrys-mod-chat-relay-script

DESCRIPTION
Free version available at the bottom of this description!
Chat between Discord and Gmod!
With this script, you can chat between the server and discord. This is handy for staff that aren't at home infront of their computer or just want to chat without joining the game. You can use it to log chat or even to warn players of an upcoming restart.

Features
Relay Text to Discord from your server's chatbox!
Blacklist abusive users from relaying messages using ULX
Enable/Disable relay chat on your client using !togglerelay
Long usernames are trimmed down to avoid creating issues with discord.
Whitelist commands allow you to specify a command to use to chat with Discord.
Relay Text to your server's chatbox from Discord!
Text is limited so it won't get too spammy.
Prevent certain commands from being parsed through the relay, such as /ooc etc.
Planned Features
Blocking abusive Discord users from sending messages
Possibly allow you to list moderator roles that can blacklist etc.
ServerGuard support
Option to use Teamchat instead of normal chat (Cinema servers treat teamchat as global chat)
Pretty-print channel names.
Adequate rate-limiting detection and proper response.
Adding prefixes and tags.
Option to customize your colors and more.
Bot commands.
Installation.
This is a massive set of instructions, so lets get started. All configuration is done in **```

 discordrelay/lua/discordrelay/server/sv_config.lua

If you have issues with following the instructions, [click here](&feature=youtu.be) for a friendly tutorial video made by [{VG} Michaela](https://scriptfodder.com/users/view/76561198022762720). Thanks Michaela! ```KEEP IN MIND SOME THINGS HAVE CHANGED, JUST REMEMBER THAT```

1. Goto [http://steamcommunity.com/dev/apikey](http://steamcommunity.com/dev/apikey) and generate an API key for your server. Give it your server's IP address. Save the key you generate to ```DiscordRelay.SteamWebAPIKey```. _Note: You don't have to give it your server's IP address, you can really give it anything you like. But I recommend your server's IP._

2. Goto [https://discordapp.com/developers/applications/me](https://discordapp.com/developers/applications/me) and create a new application. Give it a name like "Gmod Chat" or something unique. Create a bot user, and reveal its token. Paste its token into ```DiscordRelay.BotToken```.

3. Still at that page on step 2, grab your Client ID. We are going to invite your bot to your server. Open notepad or another text editor and paste **https://discordapp.com/oauth2/authorize?client_id=CHANGEME&scope=bot** into it. Change the test **CHANGEME** with the Client ID from earlier. Now paste that link into your browser. _Be sure that ```&scope=bot``` is on the end, otherwise it won't work._

4. Create a channel in your discord server (if you haven't already). Goto the channel settings and create a webhook. Don't bother naming it, we override the name for the webhook anyway. Copy the webhook URL and paste it into ```DiscordRelay.WebhookURL```.

5. In your discord chat, type ```\#yourchannelname``` and send the message. In the chat, you should now see a message that looks a bit like this: **<#12345678910111213>**. Remove the **<#** and the **>** at either end so that you only have a long number left. Paste that number into ```DiscordRelay.DiscordChannelID```.
!IMPORTANT!``` If your channel is hidden from standard users, your bot MUST be given permissions to read messages in that channel. I recommend creating a bot role for this task. Remember, if your bot cannot read the channel's messages, the server won't see them.

Additional Config Options…

DiscordRelay.ServerPrefix : This config option contains a string, which is put before every username of every player to send a message to discord. Handy if you have multiple servers pointing into one room.
DiscordRelay.MessageDelay : This config option defines how long we should wait between checking for new messages. Don't set this below 1 or 2 seconds, as discord may rate limit you and get very angry with me.
DiscordRelay.MaxMessages : This config option limits how many new messages will be printed to chat at once. Prevents spam. Max is 50.
DiscordRelay.BlockedCommands : A useful option, its an array of strings, that contains text that shouldn't be relayed. If any of these strings are detected at the start of a message, it won't be relayed.
DiscordRelay.EnableWhitelist : Enabled the whitelist feature.
DiscordRelay.WhitelistCommands : Just like BlockedCommands, only exactly opposite. This option only relays messages that start with string found in this array.
DiscordRelay.AnnounceConnect : Announces new connections in discord.
DiscordRelay.AnnounceDisconnect : Announces disconnects in discord.
DiscordRelay.AnnounceOnline : Announces when the server is ready to take connections, along with a link to connect to the server.
There are always more config options being added, all of which are available in the free version!

See it in action!
enter image description here

Support
If anything should go wrong, or you have a feature suggestion, send me a ticket. I may be a bit delayed in responding to tickets, but I will do my best.

My support reps will be more than happy to help you in my absence. They keep me informed of anything that need my attention.

Common mistakes (and how to troubleshoot them!)
My server console has red text reading "HTTP Error…" and says something after it!
This can be the cause of several issues. Make sure your server is able to ping http://discordapp.com/. If you get this error just once, its ok, that's like buying 100 paper cups and having one of them broken.
Chat has suddenly stopped being relayed into my server
You may have been rate limited. Please send us a ticket, we may have to contact Discord on your behalf. In the meantime, increase the message delay config option to 5 or more.
Someone from discord is abusing the relay, what do I do?
Currently the script doesn't feature a way to blacklist users on discord from being relayed, however it is in the works. In the meantime, I recommend creating a role on your discord server, denying it access to send messaged in your relay channel, and applying it to any abusive users. Alternatively, ban them from your discord.
I bought this script expecting to be able to blacklist users, but I use <insert unsupported admin mod> and it doesn't work!
Open a ticket, and let us know what admin mod you use. We will try to include support for it within a reasonable time-frame.
For some strange reason the Garry's Mod server isn't receiving messages. What's going on?
On your server, browse to data/discord_relay and open recieved_messages.txt. Yes, I know it's a typo. No, it doesn't matter. Anyway, if the contents of that file is literally [], then there's a problem with your bot.
Check your bot token is correct in the config. It should look like MjQ3BlAhBlaHBLaH.Al_aHu.R3AllYL0nGSt4inGOFth1ngs.
Check your channel ID is correct. When you type \#channel-name into discord, your message should turn into something like <#12345678901234>. The ID of the channel (as stored in your config) should not include <# or >.
Make sure your bot has permission to read messages in that server. If you aren't sure, ask a friend to help test it, give your volunteer the same permissions as your bot has and ask them to try and read your channel. If they cannot see the channel or its contents, your bot can't either, and thus neither can the Garry's Mod server.
If all of that fails, send me a ticket. I'm always looking for more bugs.
Known Incompatible Scripts:
This is a list of scripts that our customers have reported to be incompatible with our script, and has been verified by us to be a fault of the script and not us. If you are the script author, send me a PM when you've fixed the problem with your script.

SChat by arie
Overrides chat.AddText() and in the process prevents the relay from printing anything to the client's chat.
Several reviews of that script report that getting support is an impossible feat, and that even the DarkRP Weapon Checker is broken because of this chatbox.
If you use this chatbox, I recommend purchasing an alternative chatbox, like HatsChat2 or AtlasChat. I've confirmed both of these chatboxes work with the relay.
