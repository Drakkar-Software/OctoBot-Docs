Discord interface
=================

{% hint style="warning" %}
**CURRENTLY ON DEVELOPMENT**
{% endhint %}

OctoBot uses the Discord interface to post alerts in a discord chat.

Discord service configuration
-----------------------------

Add in **user/config.json** in the services key :

``` {.sourceCode .json}
"discord": {
       "token": "YOUR_BOT_TOKEN",
       "channel_id": "YOUR_CHANNEL_ID"
   }
```

**Exemple:**

``` {.sourceCode .json}
"services": {
   "a service": {

   },
   "discord": {
       "token": "YOUR_BOT_TOKEN",
       "channel_id": "YOUR_CHANNEL_ID"
   },
   "another service": {

   }
}
```

All the information can be found
[here](https://github.com/reactiflux/discord-irc/wiki/Creating-a-discord-bot-&-getting-a-token)
to create a Discord bot.
