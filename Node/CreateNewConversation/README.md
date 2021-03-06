# Create New Conversation Bot Sample

A sample bot that starts a new conversation using a previously stored user address.

[![Deploy to Azure][Deploy Button]][Deploy CreateNewConversation/Node]
[Deploy Button]: https://azuredeploy.net/deploybutton.png
[Deploy CreateNewConversation/Node]: https://azuredeploy.net?ptmpl=Node/CreateNewConversation/azuredeploy.json

### Prerequisites

The minimum prerequisites to run this sample are:
* Latest Node.js with NPM. Download it from [here](https://nodejs.org/en/download/).
* The Bot Framework Emulator. To install the Bot Framework Emulator, download it from [here](https://aka.ms/bf-bc-emulator). Please refer to [this documentation article](https://docs.botframework.com/en-us/csharp/builder/sdkreference/gettingstarted.html#emulator) to know more about the Bot Framework Emulator.
* **[Recommended]** Visual Studio Code for IntelliSense and debugging, download it from [here](https://code.visualstudio.com/) for free.

### Code Highlights

Bot Builder uses dialogs to model a conversational process, the exchange of messages, between bot and user. [bot.beginDialog()](app.js#L28) can be used to proactively start a new dialog to interact with the user.
Because, an address is required to initiate a new conversation, this user address should be saved during any previous conversation with the user. 
Any current conversation between the bot and user will be replaced with a new dialog stack.
Alternatively, [bot.send()](https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.universalbot.html#send) can be used to send a message without starting a dialog. 

````JavaScript
// minimal information copied from the address of a previous message
// this is the obj we should persist if we want to create a new conversation anytime later 
var address = {
    channelId: msg.address.channelId,
    serviceUrl: msg.address.serviceUrl,
    user: msg.address.user,
    bot: msg.address.bot,
    useAuth: true
};

// then... on another scope

// start survey dialog using stored address
bot.beginDialog(address, '/survey');
````

### Outcome

You will see the following when connecting the Bot to the Emulator and send it a message.

![Sample Outcome](images/outcome-emulator.png)

On the other hand, you will see the following in Skype.

![Sample Outcome](images/outcome-skype.png)

### More Information

To get more information about how to get started in Bot Builder for Node and Dialogs please review the following resources:
* [Bot Builder for Node.js Reference](https://docs.botframework.com/en-us/node/builder/overview/#navtitle)
* [Dialogs](https://docs.botframework.com/en-us/node/builder/chat/dialogs/)
* [UniversalBot.beginDialog](https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.universalbot.html#begindialog)
* [UniversalBot.send](https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.universalbot.html#send) & [IMessage interface](https://docs.botframework.com/en-us/node/builder/chat-reference/interfaces/_botbuilder_d_.imessage.html)
