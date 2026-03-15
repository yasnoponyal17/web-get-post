# Лабораторная работа 5
## Описание инструментария:
- HTML, CSS
- JavaScript (Node.js)
- Express.js

## Код script.js
```JavaScript
const express = require("express");
const path = require('path');
const app = express();

app.use(express.static(path.join(__dirname, 'public')));
const urlencodedParser = express.urlencoded({extended: false});
  
app.get("/", function (_, response) {
    response.sendFile(__dirname + "/index.html");
});
app.post("/", urlencodedParser, function (request, response) {
    if(!request.body) return response.sendStatus(400);
    console.log(request.body);
    response.send(`${request.body.userName} - ${request.body.userAge}`);
});
   
app.listen(3000, ()=>console.log("Сервер запущен..."));
```

## Работа в браузере
### GET-запрос
![Browser GET](./images/browser-get.png)
### POST-запрос
![Browser POST](./images/browser-post.png)

## Работа через cURL
### GET-запрос
![cURL GET](./images/curl-get.png)
### POST-запрос
![cURL POST](./images/curl-post.png)

## Работа через Postman
### GET-запрос
![Postman GET](./images/postman-get.png)
### POST-запрос
![Postman POST](./images/postman-post.png)

### Ефимов Сергей Робертович, 2 курс, ИВТ-2