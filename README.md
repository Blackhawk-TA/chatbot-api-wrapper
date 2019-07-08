# dynoBot-Framework
[![license](http://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/Blackhawk-TA/dynoBot-Framework/blob/master/LICENSE.md)
[![Build Status](https://travis-ci.com/Blackhawk-TA/dynoBot-Framework.svg?branch=master)](https://travis-ci.com/Blackhawk-TA/dynoBot-Framework)
[![npm](https://img.shields.io/npm/v/dynobot-framework.svg?color=brightgreen)](https://www.npmjs.com/package/dynobot-framework)
[![github](https://img.shields.io/github/release/Blackhawk-TA/dynoBot-Framework.svg?color=brightgreen)](https://github.com/Blackhawk-TA/dynoBot-Framework/releases)
[![github](https://img.shields.io/github/package-json/v/Blackhawk-TA/dynoBot-Framework/master.svg?color=blue)](https://github.com/Blackhawk-TA/dynoBot-Framework/tree/master)
[![github](https://img.shields.io/github/package-json/v/Blackhawk-TA/dynoBot-Framework/development.svg?color=blue)](https://github.com/Blackhawk-TA/dynoBot-Framework/tree/development)

### Overview
1. [dynoBot-Framework](#dynobot-framework)
2. [Documentation](#documentation)
3. [Setup](#setup)
4. [Events](#events)
4. [Implementation](#implementation)

### dynoBot-Framework
dynoBot-Framework is an chat bot api wrapper which allows you to code your bot independently from chat bot APIs such as the ones from discord or slack.
Currently only discord bots are supported. Slack will follow soon.

### Documentation
You can find a documentation for the dynoBot-Framework here:

http://dynodoc.tapadventures.com/

### Setup
`npm install dynobot-framework`

Now you can use the framework by adding following line:
```js
const {DiscordBot} = require("dynobot-framework");
```

### Events
Supported events:
- `error` - returns Error object
- `serverMemberAdd` - returns User object
- `serverMemberRemove` - returns User object
- `message` - returns Message object
- `ready` - no return value

Events can be used like this:
```js
Bot.getClient().onEvent("<event-name>", (returnValue) => {
	//Code that shall be executed when the event was triggered
});
```

### Implementation
There is an open source bot called [dynoBot](https://github.com/Blackhawk-TA/dynoBot) which uses the dynoBot-Framework.
You can take a look at it if you prefer a more realistic implementation example.

There is also an example of a simple bot implementation to get started withk:
```js
const {DiscordBot} = require("dynobot-framework");
const Bot = new DiscordBot("<discord-token>");

Bot.getClient().onEvent("ready", () => {
	console.log("Bot started");

	Bot.getClient().onEvent("message", (msg) => {
		if (msg.isMentioned(Bot.getClient().getUser())) {
			msg.getChannel().send("OK");
		}
	});
});
```