<img src="https://github.com/mail-ru-im/bot-python/blob/master/logo.png" width="100" height="100">

# Golang interface for ICQ bot API

## Install
```bash
go get github.com/DmitryDorofeev/goicqbot
```

## Usage

Create your own bot by sending the /newbot command to Metabot and follow the instructions.

Note a bot can only reply after the user has added it to his contact list, or if the user was the first to start a dialogue.

### Create your bot

```go
package main

import "github.com/DmitryDorofeev/goicqbot"

func main() {
    bot := goicqbot.NewBot(BOT_TOKEN)

    bot.SendMessage(&goicqbot.Message{Text: "text", ChatID: "awesomechat@agent.chat"})
}
```

### Send message

```go
message := &goicqbot.Message{Text: "text", ChatID: "awesomechat@agent.chat"}
bot.SendMessage(message)

fmt.Println(message.MsgID)
```

### Subscribe events

```go
ctx, finish := context.WithCancel(context.Background())
updates := bot.GetUpdatesChannel(ctx)
for update := range updates {
	// your awesome logic here
}
```

### Passing options

You can override bot's API URL:

```go
bot := goicqbot.NewBot(BOT_TOKEN, goicqbot.BotApiUrl("https://agent.mail.ru/bot/v1"))
```

And debug all api requests and responses:

```go
bot := goicqbot.NewBot(BOT_TOKEN, goicqbot.BotDebug(true))
```


## Roadmap

- [x] Send message

- [x] Events subscription

- [x] Tests

- [x] Godoc

- [x] Edit message

- [ ] Send files

- [ ] Send voice

- [ ] Delete message
