## Web Chat in Development

Web Chat in Development is designed to be a simple set-up-and-go implementation of [BotFramework-WebChat](https://github.com/microsoft/botframework-webchat) allowing the developer, with minimal effort, to run a development instance of Web Chat without requiring deployment. The components contained within include a `webchat.html` page as well as two servers: `tokenServer.js` and `webServer.js`.

### Requirements

- [Node.js](https://nodejs.org/en/) installed on your system
- A locally deployed [bot](https://docs.botframework.com) running on (default) port `3978`
- An Azure [bot registration](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-quickstart-registration?view=azure-bot-service-3.0)
- Either [ngrok](https://blog.botframework.com/2017/10/19/debug-channel-locally-using-ngrok/) or [Azure Service Bus](https://blog.botframework.com/2019/04/16/debugging-your-locally-hosted-v4-bot-using-azure-relays/) installed on your system
- [Python](https://www.python.org/downloads/) v3.5+ installed on your system
  - The [Twisted](https://pypi.org/project/Twisted/) package  installed on your system - installed via the `pip` command (`pip install Twisted`)
    - *If any errors are generated while installing Twisted, please refer to the alternative installation steps proposed [here](https://stackoverflow.com/a/62276435/3962636)*
    - *Per the proposed alternative installation steps, to determine the correct .whl file to download  run the following two commands, as described [here](https://stackoverflow.com/a/63775417/3962636):*
  
      `python --version`

      `python bitness: python -c "import struct; print(struct.calcsize('P') * 8)"`

#

### Setting up
- Clone this repo and run `npm i` in the root directory
- Update the `.env` file with:
  - Your Direct Line secret, which can be obtained by adding the Direct Line channel in your bot's Channels blade in Azure. Copy the key supplied there.
  - The port to use for the token server.
  - The path to be used as the web server's root directory.
  - The port to use for the web server.

#

### Running Web Chat in Development
- Start your bot locally on your machine
- Start up ngrok, Azure Service Bus Relay, or equivalent, using port `3978` to create a tunnel
  - Update the bot registration's messaging endpoint with the generated endpoint (ngrok example: `https://j8dhs7elw.ngrok.io/api/messages`)
- Type `npm run watch` to run both servers concurrently
- Navigate to [http://localhost:8000](http://localhost:8000) to test your bot and/or Web Chat