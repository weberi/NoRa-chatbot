

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

   ### Webchat Integration

To enable users to chat with your bot via a web interface, you can use a webchat like [my_chatroom](https://weberi.github.io/my_chatroom.github.io). Follow these steps to integrate the chatroom with your bot running in the Codespace:


1. **Expose Rasa Port**: After running the Rasa command in your Codespace (```rasa run --port 5005 --cors "*"````) and making port 5005 public, your Codespace will generate a public URL for your Rasa server. This URL should look something like:

```https://your-codespace-url-5005.preview.app.github.dev```

2. **Create a Chatroom **: Clone the repo  [https://weberi.github.io/my_chatroom.github.io](https://weberi.github.io/my_chatroom.github.io) It will let you setup a web page showing a chatroom.

3. **Configure the Chatroom**: Direct the webchat to communicate with your Rasa instance by providing this public URL to the chatroom's configuration. If you're using [my_chatroom](https://weberi.github.io/my_chatroom.github.io), you need to configure it to point to your Rasa instance’s URL.

- Open the `index.html` file in the `my_chatroom` repository (or your equivalent webchat interface).
- Find the part where it connects to the Rasa server. This is usually a script or configuration block that contains a URL. Replace the placeholder URL with the public URL of your Codespace's Rasa instance (the one from step 1).

The configuration might look something like this:

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
        host: https://your-codespace-url-5005.preview.app.github.dev",   <!-- replace here !!!>
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

Now, start chatting with the bot!

