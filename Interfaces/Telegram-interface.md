Telegram interface
==================

OctoBot uses the Telegram interface to communicate. With this interface, OctoBot can:

-   Show for how long OctoBot is working
-   Display the current portfolio
-   Display the current open orders
-   Display the profitability since OctoBot started
-   Display OctoBot's understanding of the market and its risk parameter
-   Changes OctoBot's current risk
-   Stop OctoBot
-   Trigger emergency trades

And much more.

To know the full command list, use the **/help** command

Telegram service configuration
------------------------------

Create your bot
---------------

See tutorial on [telegram
website](https://core.telegram.org/bots#6-botfather)

Configuration
-------------

![telegram config](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/telegram_config.png)

### Token

Get the token in the chat with **botfather** and add it to services config

### Chat id

Send a message to your bot and go to this url <https://api.telegram.org/botXXX:YYYY/getUpdates> with XXX:YYYY replaced by your bot's token.

Warning: To get your chat id from this url, your telegram bot must have a pending message (the one you just sent). This means that your OctoBot must not be on or you will just receive this message `{"ok":true,"result":[]}` from api.telegram.org.

Search for:

``` bash
chat:
    id: XXXXXXXXX
```

Add this id to the telegram service configuration.

Allow your bot to listen to telegram groups and channels
--------------------------------------------------------

OctoBot can receive messages (trade signals for example) from Telegram groups.

When invited in a Telegram group, OctoBot will never talk in this group but will listen to the chat. Using this feature, it is possible to process **telegram signals** in OctoBot.

In order to be able to read group messages, your telegram bot must have its **privacy mode** **disabled**. To disable it:

-   say `/setprivacy` to **botfather**
-   **botfather** replies: *Choose a bot to change group messages settings.*
-   enter the name of your bot
-   **botfather** gives information about privacy mode and your bot's privacy setting
-   enter `Disable`

Your OctoBot is now able to read any group message.


user/confg.json configuration
-----------------------------

Add in **user/config.json** in the services key :

``` json
"telegram": {
       "chat-id": "YOUR_CHAT_ID",
       "token": "YOUR_BOT_TOKEN"
   }
```

**Exemple:**

``` json
"services": {
   "a service": {

   },
   "telegram": {
       "chat-id": "YOUR_CHAT_ID",
       "token": "YOUR_BOT_TOKEN"
   },
   "another service": {

   }
}
```

Troubleshooting
---------------

### Chat not found

If OctoBot is producing this you get this error, it means that your [chat-id](#chat-id) is not set correctly. With an incorrect chat-id, OctoBot is able to read and reply commands but can't push messages by itself.

### TelegramSignalEvaluator is not receiving telegram messages

To use the default Telegram signal evaluator, make sure:

1.  Your telegram group / channel is referenced in the TelegramSignalEvaluator configuration
2.  Your telegram bot is setup according to [Allow your bot to listen to telegram groups and channels](#allow-your-bot-to-listen-to-telegram-groups-and-channels)
3.  Your telegram bot is in the telegram channel / group
4.  The telegram notifications you want your bot to process are matching the notification pattern defined in the TelegramSignalEvaluator documentation
5.  The telegram signal trading pairs also are traded pairs in your current OctoBot configuration and are supported by the connected exchange(s)
6.  Your TelegramSignalEvaluator is activated

When a telegram message is ignored, a debug log (in terminal and OctoBot.log) is produced explaining the reason why each notifications has be ignored. Please first refer to this log as it will likely show what is wrong with the current setup.
