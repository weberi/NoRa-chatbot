

# NoRa Chatbot

A transactional chatbot built with **Rasa OpenSource** for chatting and **Node-RED** for actions, running on a **Codespace**.

## Getting Started

You can fork this repository and run the chatbot on your own Codespace!

### The Repository provides a setup for

- a [GitHub Codespace](https://github.com/features/codespaces)
- a Rasa OpenSource powered chatbot
- an action server for the chatbot running on Node-RED using  [node-red-contrib-rasa-actionserver](https://github.com/weberi/node-red-contrib-rasa-actionserver) nodes

### Setup Instructions

1. **Fork the Repository**: Click the fork button at the top right of this page.
2. **Open in Codespace**: Once forked, open the repository's Codespace in the browser. This may take up to 10 minutes.
3. In the terminal of the Codespace: ```cd moodbot```, then type ```rasa train``` and hit Enter. When the training is complete:
4. **Start Rasa**: In the terminal, run the following command to start Rasa:

   ```rasa run --port 5005 --cors "*"```

5. **Expose Rasa Port**: After starting the Rasa service, your Codespace will open port **5005** and provide a URL for your Rasa service in your Codespace. You can find this in the **Ports** tab. Change the port visibility from  *Private* to *Public*. The URL should look something like: ```https://your-codespace-url-5005.preview.app.github.dev```. Make sure to publish the URL for port **5005**. There will be a second port, **1880**, , which is used by your Node-RED action server and can remain *Private*.

Now, your bot is running, you can chat with it, e.g., via a chatroom.


### Talk with the bot in a Chatroom or WebChat

You can create a local Chatroom as follows:

1. **Make a local Chatroom**: Copy the following code and save it as text file,  e.g., ```index.html```, on your local PC.
```
<!DOCTYPE html>
<html lang="en">

<head>
    <link rel="stylesheet" href="https://cdn.statically.io/gh/weberi/chatroom/master/dist/Chatroom.css" />
    <link rel="stylesheet" type="text/css" href="https://cdn.statically.io/gh/weberi/chatroom/master/index.css">
    <link rel="stylesheet" type="text/css" href="https://cdn.statically.io/gh/weberi/chatroom/master/themes/theme2.css" />
</head>
<body>
    <div class="chat-container"></div>
    <script src="https://cdn.statically.io/gh/weberi/chatroom/master/dist/Chatroom.js"></script>
    <script type="text/javascript">
    var chatroom = new window.Chatroom({
        host: "https://your-codespace-url-5005.preview.app.github.dev",   
        title: "Chat with a bot",
        container: document.querySelector(".chat-container"),
        welcomeMessage: "Nice to meet you.",
        speechRecognition: "en-US",
        voiceLang: "en-US"
    });
    chatroom.openChat();
    </script>
</body>
</html>
```
2. **Configure the Chatroom**: Direct the chatroom to communicate with your Rasa service by providing this public URL to the chatroom's configuration. To do this,
replace the placeholder URL in the ```host``` value with the public URL that you exposed in your Codespace (the one from step 5 above).  Ensure that the URL is enclosed in quotes, and remove any trailing  ```\``` if it appears.
3. **Open the Chatroom**: Save the ```index.html``` again and open it in a browser.

Now, start chatting with the bot!

