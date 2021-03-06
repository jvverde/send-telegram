# Send a telegram from a CLI
Send messages from a linux shell

### Requirements

You should have **curl** installed

### Installation

* On your Telegram client search (global) for BotFather
* Send it the command */newbot* and start a conversation with it, namely:
  * Choose a bot name (ex: *Alerts*)
  * Choose a username ending with Bot (ex: *somethingBot*)
  * If everything is ok it will return a congratulations messages which includes a HTTP API Token. Something like this **123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11**
  * Save that Token to a private and secure place
  * Go to the Global search again, and search for your boot (ex: *somethingBot*)
  * Send it the command */start*
  * Send a message to it (ex: Hello)

Now open a shell and clone this git repository
```bash
git clone https://github.com/jvverde/send-telegram ${HOME}/telegram
```
Go to ${HOME}/telegram
```bash
cd ${HOME}/telegram
```
Open another bash shell (by secure reasons)
```bash
bash
```
Set an environment variable TOKEN="*123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11*" (use the token saved above)
```bash
TOKEN="POST_YOUR_TOKEN_HERE"
```
Check the new messages on your bot (You should have at least one if you had sent a message *Hello* on previous step)
```bash
curl https://api.telegram.org/bot$TOKEN/getUpdates
```
You shoud receive a json object. Look for the something like this
```bash
...,"chat":{"id":822330591,"first_name":...
```
( If you only obtain a message like this ``` {"ok":true,"result":[]} ``` it means you haven't send a message yet. Go to client and send a *Hello* messages to your bot and try again )

Take note of the value on field **id** of **chat** and then copy **.env.example** to **.env**

```bash
cp .env.example to .env
```
Edit **.env** with your prefered editor
```bash
vim .env
```
And set the variables *TOKEN* and *CHAT_ID* with the previous obtained values.

Save the **.env**

Now test it by send a *Hello World* message
```bash
./send-telegram.sh "Hello World"
```
If everything is ok you should have received a *Hello World* on you telegram client

Now exit from you bash tin order o discart TOKEN variable from environment 
```bash
exit
```
Send a second messages
```bash
./send-telegram.sh "My second message"
```

Thats it!


