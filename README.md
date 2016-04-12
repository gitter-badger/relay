# relay
Bot user that can send messages to different users

# Inspiration
Botkit easily handles responding to messages from users. However, it sometimes fails when responses are delayed.

I could not find an easy way to handle this.
* No easy way to send a "typing ..." notification
* No easy way to send multiple messages with delay in between, to a specific user.

# Covered
* Turn the bot on and off.
 * slack RTM api provides a way to do this by use of a channel-id
```javascript

```
 * relay provide a "notify" method that takes in the user-name or channel-name
```javascript
const relay = require('bot-relay');
let token = '<slack bot token>'; //@TODO add url to get this token
let slackRelay = relay.slackRelay(token);

slackRelay.connect().then( relayInstance => {
  // notify users that you are about to post/send a message
  // use-case lookup last deployed version and post it to this channel
  relayInstance.notify('user_typing');
  lookupDeployedVersion('github-repo').then(project => {
    relayInstance.post(`currently deployed version for ${project.name} is ${project.version}`);
  });

}, connectionError => {
  // you can try to reconnect
  // you can verify with slack to make sure your token is still valid
});
```
 
* Send message to slack user
 * given user name or IM(= slack's channel id for direct messages) id
 * use your bot info (bot id, bot username) to send a message to the above user.
```javascript

```

* Post in a slack channel
 * given a channel name 
 * use your bot info (bot id, bot username) to post a message to the above channel.
```javascript

```
 
 
