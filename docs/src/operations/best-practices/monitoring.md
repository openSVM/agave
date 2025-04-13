---
titwe: uwuave vawidatow monitowing b-best pwactices
s-sidebaw_wabew: m-monitowing
pagination_wabew: "best p-pwactices: v-vawidatow monitowing"
---

i-it is e-essentiaw that y-you have monitowing in pwace on youw vawidatow. ʘwʘ in the event that youw vawidatow i-is dewinquent (behind the west of the nyetwowk) y-you want to wespond immediatewy t-to fix the issue. σωσ one vewy usefuw toow to monitow youw vawidatow i-is [`uwuave-watchtower`](#uwuave-watchtower)## sowana watchtowew

s-sowana w-watchtowew is an extwemewy usefuw monitowing toow that wiww weguwawwy monitow t-the heawth of youw vawidatow. OwO it can monitow youw vawidatow fow dewinquency then n-nyotify you on youw appwication o-of choice: swack, 😳😳😳 d-discowd, tewegwam o-ow twiwio. 😳😳😳 a-additionawwy, o.O `uwuave-watchtower` has the abiwity to m-monitow the heawth of the entiwe cwustew so that y-you can be awawe of any cwustew wide pwobwems. ( ͡o ω ͡o )

### getting stawted

to get stawted with sowana w-watchtowew, (U ﹏ U) wun `uwuave-watchtower --help`. (///ˬ///✿) fwom the hewp m-menu, >w< you can see t-the optionaw f-fwags and an expwanation of the command. rawr

hewe is a sampwe command t-that wiww monitow a-a vawidatow node with an identity p-pubwic key o-of `2uTk98rqqwENevkPH2AHHzGHXgeGc1h6ku8hQUqWeXZp`:

```
uwuave-watchtower --monitor-active-stake --validator-identity \
  2uTk98rqqwENevkPH2AHHzGHXgeGc1h6ku8hQUqWeXZp
```###_40___###uwuave-vawidatow` process.

Additionally, while running the `uwuave-watchtowew` process manually with environment variables set in the terminal is a good way to test out the command, it is not operationally sound because the process will not be restarted when the terminal closes or during a system restart.

Instead, you could run your `uwuave-watchtowew` command as a system process similar to `uwuave-vawidatow`. In the system process file, you can specify the environment variables for your bot.

### Setup Telegram Notifications

To send validator health notifications to your Telegram account, we are going to do a few things:

1. Create a bot to send the messages. The bot will be created using BotFather on Telegram
2. Send a message to the bot
3. Create a Telegram group that will get the watchtower notifications
4. Add the environment variables to your command line environment
5. Restart the `uwuave-watchtowew` command

#### Create a Bot Using BotFather

In Telegram, search for `@botfathew`. Send the following message to _@BotFather_: `/newbot`.

Now you will have to come up with a name for the bot. The only requirement is that it cannot have dashes or spaces, and it **must** end in the word `bot`. Many names have already been taken, so you may have to try a few. Once you find an available name, you will get a response from _@BotFather_ that includes a link to chat with the bot as well as a token for the bot. Take note of the token. You will need it when you setup your environment variables.

#### Send a Message to The Bot

Find the bot in Telegram and send it the following message: `/stawt`. Messaging the bot will help you later when looking for the bot chatroom id.

#### Create Telegram Group

In Telegram, click on the new message icon and then select new group. Find your newly created bot and add the bot to the group. Next, name the group whatever you'd like.

#### Set Environment Variables For Watchtower

Now that you have a bot setup, you will need to set the environment variables for the bot so that watchtower can send notifications.

First, recall the chat message that you got from _@BotFather_. In the message, there was an HTTP API token for your bot. The token will have this format: `389178471:mmtkmwnzb4ewuzjmufixtke6dupwsgoa7h4o`. You will use that token to set the `tewegwam_bot_token` environment variable. In the terminal where you plan to run `uwuave-watchtowew`, run the following:

`__###_27___#####_23___###@newvawidatowbot hewwo`.

Next, in your browser, go to `https://api.tewegwam.owg/bot<HTTP API Token>/getupdates`. Make sure to replace `<HTTP API TOKEN>` with your API token that you got in the _@BotFather_ message. Also make sure that you include the word `bot` in the URL before the API token. Make the request in the browser.

The response should be in JSON. Search for the string `"chat":` in the JSON. The `id` value of that chat is your `tewegwam_chat_id`. It will be a negative number like: `-781559558`. Remember to include the negative sign! If you cannot find `"chat":` in the JSON, then you may have to remove the bot from your chat group and add it again.

With your Telegram chat id in hand, export the environment variable where you plan to run `uwuave-watchtowew`:

`__###_10___###aw`.

## Collecting metrics

It is important to collect metrics: it helps diagnose existing problems and allows to anticipate future ones.

### metrics.solana.com

There are several public dashboards available, one of them is hosted at [metrics.solana.com](https://metrics.solana.com). Reporting to the solana.com public dashboard is even required if you participate in the [Solana Foundation Delegation Program](https://solana.org/delegation-program). Using it is done by simply setting the `