---
title: "Facebook chatbot using watson assistant"
layout: post
date: 2019-01-06 14:30
tag: JavaScript
image: https://1.bp.blogspot.com/-26-xe6D3FLQ/Wap6HvV-GzI/AAAAAAAAaUw/au_ObmqNYNU7ezm0NYljXs3pDHOVgONBACPcBGAYYCw/s1600/TexttoSpeech.png
headerImage: true
projects: true
hidden: true # don't count this post in blog pagination
description: "This is a simple facebook chatboot using Watson Assistant by IBM"
category: project
author: johndoe
externalLink: false
---

The main idea of this project is show how to connect a facebook chatboot in NodeJS with Watson Assistant.

---

# What do you need?
- NodeJS
- Bluemix account
- Facebook Page
- Coffe

---

# Step 1: Initilize your Node.js app

First of all you have to create a new directory for your Node.JS application. Open yor file explorer or command prompt and type: 

```
mkdir AnAwesomeName
cd AnAwesomeName
```
Then you have to run on command prompt this line:

```
npm init
```

# Step 2: Install Express.js in your application folder

While command prompt path stills in your Node.js application folder, run this line:

```
npm install express --save
```

# Step 3: Start your favorite text editor (You can use [Visual Studio Code](https://code.visualstudio.com/) or [Atom](https://atom.io/))

Open index.js and replace all that contains with this code:

```javascript
var bodyParser=require('body-parser');
var request=require('request');
var express = require('express');var watson = require('watson-developer-cloud');
var assistant = new watson.AssistantV1({
    username: 'Paste Assistan api username here',
    password: 'paste Assistan api password here',
    version: '2018-07-10'
});

var app = express();
app.use(bodyParser.json());
const APP_TOKEN='Paste your Facebook token here';

app.get('/', function (req, res) {
  res.send('Hello World!');
});
app.get('/webhook',function(req,res){
    if(req.query['hub.verify_token']=='Paste your Facebook Token Here '){
        res.send(req.query['hub.challenge']);
    }else{
        res.send('You cant access here ): ');
    }
});
//valida eventos
app.post('/webhook',function(req,res){
    var data=req.body;
    
    if(data.object=='page'){
        data.entry.forEach(function(pageEntry){
            pageEntry.messaging.forEach(function(messagingEvent){
                if(messagingEvent.message){
                reciveMessage(messagingEvent);
                }
            });
        });
        res.sendStatus(200);
    }//end if
});

////////////////////
//recive mensaje
function reciveMessage(event){//this function recive message an
    var senderID=event.sender.id;
    var messageText=event.message.text;
    //console.log(senderID);
    //console.log(messageText);
    sendTextToWatson(senderID,messageText);
}


function sendTextToWatson(senderId,inputText) { //This function call to Assitan api en get the answer :v
    var finalMessage='';
    assistant.message({
        workspace_id: 'Pase your workspace id here',
        input: { 'text': inputText }
    }, function (err, response) {
        if (err){
            finalMessage=err;
            //console.log('error:', err);
        }
        else{
            finalMessage=response.output.text[0];
            //console.log(JSON.stringify(response, null, 2));
            console.log("sendTextToWatson        "+finalMessage);
        }
        sendMessageText(senderId,finalMessage);

    });
}


function sendMessageText(recipientId,message){ //this function format the message
    var messageData={
        recipient:{
            id:recipientId
        },
        message:{
            text:message
        }
    };
    callSendApi(messageData);
}

function callSendApi(messageData){ //This function send text message to facebook 
    request({
        uri:'https://graph.facebook.com/v2.6/me/messages',
        qs:{access_token:APP_TOKEN},
        method:'POST',
        json:messageData
    },function(error,response,data){
        if(error){
            console.log('Error enviando msg');
        }else{
            console.log('Mensaje exitoso');
        }
    });
}
////////
var host = (process.env.VCAP_APP_HOST || 'localhost');
var port = (process.env.VCAP_APP_PORT || 3000);
app.listen(port, host);

```
---
# Step 4: Add Watson Assistant to your Package.json

Your package.json maybe looks like this:

```json

{
	"name": "NodejsStarterApp",
	"version": "0.0.1",
	"private": true,
	"scripts": {
		"start": "node app.js"
	},
	"dependencies": {
		"express": "4.15.x",
		"cfenv": "1.0.x",
		"body-parser": "1.15.0", //Only copy this line,
		"request": "2.72.0",      // and this,
		"htmlparser": "1.7.7",    //and this,
		"watson-developer-cloud": "^3.7.0"// and finally this. Please ignore everything else.
	},
	"repository": {},
	"engines": {
		"node": "6.x"
	} 
}

```

---
# Step 5: Configure Facebook pages

Finilly you have to configure your webhook and your facebook token with that of your index.js

---

You can find code files [here](https://gist.github.com/devmaufh/)

---
