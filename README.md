# DummyAPI

Здесь представлено описание тестирования проекта [dummyapi.io](https://dummyapi.io/)

## Оглавление

1. [Описание проекта](#описание-проекта)
   1. [USER](#user)
        1. [GET /user (Get List)](#get-user--get-list)
        2. [GET /user/:id (Get User data by ID)](#get-userid-get-user-data-by-id)
        3. [POST /user/create (Create New User)](#post-usercreate-create-new-user)
        4. [PUT /user/:id (Update User)](#put-userid-update-user)
        5. [DELETE /user/:id (Delete User)](#put-userid-update-user)
        6. [Майнд-карта DummyAPI_User](#майнд-карта-dummyapi_user)
   2. [POST](#post)
        1. [GET /post (Get Post List)](#get-post-get-post-list)
        2. [POST /post/create (Create New Post)](#post-postcreate-create-new-post)
        3. [Майнд-карта DummyAPI_Post](#майнд-карта-dummyapi_post)
2. [Тест-кейсы](#тест-кейсы)
3. [Баг-репорты](#баг-репорты)
4. [Коллекции POSTMAN](#Коллекции-POSTMAN)
5. [Автотесты](#Автотесты)

## Описание проекта

[Dummyapi.io](https://dummyapi.io/) - этот проект представляет собой сервис для тестирования API. Он устроен как социальная сеть с пользователями, постами, тегами и комментариями. Для выполнения запросов необходим app-id, который генерируется автоматически в личном кабинете после регистрации на сайте. Для тестирования  выбраны объекты [**User**](#user) и [**Post**](#post).

### USER
___
#### GET /user  (Get List)

Возвращает список пользователей, осортированных по дате регистрации. 
- доступны query params для вывода определенной страницы,
- доступны query params для отображения определенного количества пользователей на странице.

**Response body:**  

**List**
```javascript
{
data: Array(Model)
total: number(total items in DB)
page: number(current page)
limit: number(number of items on page)
}
```

**User preview**
```javascript
{
id: string(autogenerated)
title: string("mr", "ms", "mrs", "miss", "dr", "")
firstName: string(length: 2-50)
lastName: string(length: 2-50)
picture: string(url)
}
```
___
#### GET /user/:id (Get User data by ID)

Возвращает инфо об определенном пользователе и инфо о его местонахождении. Необходим ID существующего пользователя.

**Response body:**  

**User Full**

```javascript
{
id: string(autogenerated)
title: string("mr", "ms", "mrs", "miss", "dr", "")
firstName: string(length: 2-50)
lastName: string(length: 2-50)
gender: string("male", "female", "other", "")
email: string(email)
dateOfBirth: string(ISO Date - value: 1/1/1900 - now)
registerDate: string(autogenerated)
phone: string(phone number - any format)
picture: string(url)
location: object(Location)
}
```

**Location**

```javascript
{
street: string(length: 5-100)
city: string(length: 2-30)
state: string(length: 2-30)
country: string(length: 2-30)
timezone: string(Valid timezone value ex. +7:00, -1:00)
}
```
___
#### POST /user/create (Create New User)

Создает нового пользователя. Возвращает информацию о вновь созданном пользователе.

**Request  body:**  

**User Full**

```javascript
{
id: string(autogenerated)
title: string("mr", "ms", "mrs", "miss", "dr", "")
firstName: string(length: 2-50)
lastName: string(length: 2-50)
gender: string("male", "female", "other", "")
email: string(email)
dateOfBirth: string(ISO Date - value: 1/1/1900 - now)
registerDate: string(autogenerated)
phone: string(phone number - any format)
picture: string(url)
location: object(Location)
}
```

**Location**

```javascript
{
street: string(length: 5-100)
city: string(length: 2-30)
state: string(length: 2-30)
country: string(length: 2-30)
timezone: string(Valid timezone value ex. +7:00, -1:00)
}
```

**Response body:**  

**User Full**

```javascript
{
id: string(autogenerated)
title: string("mr", "ms", "mrs", "miss", "dr", "")
firstName: string(length: 2-50)
lastName: string(length: 2-50)
gender: string("male", "female", "other", "")
email: string(email)
dateOfBirth: string(ISO Date - value: 1/1/1900 - now)
registerDate: string(autogenerated)
phone: string(phone number - any format)
picture: string(url)
location: object(Location)
}
```
___
#### PUT /user/:id (Update User)

Обновляет информацию о существующем пользователе. Необновляемые поля: id, email, registerDate, updatedDate. Возвращает информацию о пользователе.

**Request  body:**  

**User Full**

```javascript
{
id: string(autogenerated)
title: string("mr", "ms", "mrs", "miss", "dr", "")
firstName: string(length: 2-50)
lastName: string(length: 2-50)
gender: string("male", "female", "other", "")
email: string(email)
dateOfBirth: string(ISO Date - value: 1/1/1900 - now)
registerDate: string(autogenerated)
phone: string(phone number - any format)
picture: string(url)
location: object(Location)
}
```

**Location**

```javascript
{
street: string(length: 5-100)
city: string(length: 2-30)
state: string(length: 2-30)
country: string(length: 2-30)
timezone: string(Valid timezone value ex. +7:00, -1:00)
}
```

**Response body:**  

**User Full**

```javascript
{
id: string(autogenerated)
title: string("mr", "ms", "mrs", "miss", "dr", "")
firstName: string(length: 2-50)
lastName: string(length: 2-50)
gender: string("male", "female", "other", "")
email: string(email)
dateOfBirth: string(ISO Date - value: 1/1/1900 - now)
registerDate: string(autogenerated)
phone: string(phone number - any format)
picture: string(url)
location: object(Location)
}
```
___
#### DELETE /user/:id (Delete User)

Удаляет пользователя по id. Возвращает ответ с id удаленного пользователя.

**Response body:**  

```javascript
{
id: string
}
```

#### Майнд-карта DummyAPI_User

В майнд-карте представлен набор тестов для тестирования объекта **USER**. Подробная проверка расписана для запросов **Get List** и **Update User**

![Майнд-карта объекта User](https://i.imgur.com/kauJneC.jpeg)

Скачать [Майнд-карту](https://github.com/katyakima/DummyAPI/blob/main/DummyAPI_User.xmind) в формате *.xmind

### POST
___
#### GET /post (Get Post List)

Возвращает список постов, осортированных по дате регистрации. 
- доступны query params для вывода определенной страницы,
- доступны query params для отображения определенного количества постов на странице.

**Response body:**  

**List**
```javascript
{
data: Array(Model)
total: number(total items in DB)
page: number(current page)
limit: number(number of items on page)
}
```

**Post preview**

```javascript
{
id: string(autogenerated)
text: string(length: 6-50, preview only)
image: string(url)
likes: number(init value: 0)
tags: array(string)
publishDate: string(autogenerated)
owner: object(User Preview)
}
```
___
#### POST /post/create (Create New Post)

Создает новый пост. Поля обязательные к заполнению: text, owner. Возвращает информацию о вновь созданном посте и его пользователе создателе.

**Request  body:**  

**Post**

```javascript
{
id: string(autogenerated)
text: string(length: 6-1000)
image: string(url)
likes: number(init value: 0)
link: string(url, length: 6-200)
tags: array(string)
publishDate: string(autogenerated)
owner: object(User Preview)
}
```

**Response body:**

```javascript
{
id: string(autogenerated)
text: string(length: 6-1000)
image: string(url)
likes: number(init value: 0)
link: string(url, length: 6-200)
tags: array(string)
publishDate: string(autogenerated)
owner: object(User Preview)
}
```

**User preview**
```javascript
{
id: string(autogenerated)
title: string("mr", "ms", "mrs", "miss", "dr", "")
firstName: string(length: 2-50)
lastName: string(length: 2-50)
picture: string(url)
}
```

#### Майнд-карта DummyAPI_Post

В майнд-карте представлен набор тестов для тестирования объекта **POST**. Подробная проверка расписана для запросов **Get Post List** и **Create Post**

![Майнд-карта объекта User](https://i.imgur.com/jRAWZsv.jpeg)

Скачать [Майнд-карту](https://github.com/katyakima/DummyAPI/blob/main/DummyAPI_Post.xmind) в формате *.xmind

## Тест-кейсы

В этой [Google.Таблице](https://docs.google.com/spreadsheets/d/1mTMu9f7VMrH6kGZej4_bimZa1AZvG6hpIVeUP13V-3c/edit?usp=sharing) представлены примеры оформления Чек-листов и Тест-кейсов к  проекту DummyAPI. Более подробно рассмотрены объекты: UPDATE User, UPDATE User Location и DELETE User.

## Баг-репорты

В данной [Google.Таблице](https://docs.google.com/spreadsheets/d/10XM0h7lcIhxQVV0z4RD2aIAfaBfj4bBh8bFTQ33ZNSg/edit?usp=sharing) представлены примеры баг-репортов, найденных при тестировании проекта DummyAPI.

## Коллекции POSTMAN

Здесь представлена [Коллекция POSTMAN](https://github.com/katyakima/DummyAPI/blob/main/DummyAPI.postman_collection.json) с тестированием объектов **User** и **Post**, а так же [окружение](https://github.com/katyakima/DummyAPI/blob/main/DummyAPI.postman_environment.json) для тестирвоания проекта DummyAPI.

## Автотесты

[Коллекция](https://github.com/katyakima/DummyAPI/blob/main/Post.postman_collection.json) из автотестов, созданных в POSTMAN и [окружение](https://github.com/katyakima/DummyAPI/blob/main/DummyAPI.postman_environment.json).
Была создана серия из автотестов по разным запросам для объекта **Post**

### GET /post (Get Post List)

С помощью сниппетов было создано 12 тестов для проверки: статус-кода, времени ответа, соотвествие структуры тела ответа массиву, количство данных в массиве, проверка некоторых полей, проверка количества ответов на одной странице и т.п.

![Ответы для запроса GETPostList](https://i.imgur.com/j07d5Ki.jpeg)

### CREATE /post (Create New Post)

Было создано 25 тестов с проверкой обязательных и необязательных полей для заполнения, массива тегов, объекта owner (создатель поста) и была проведена проверка на отсутствие отображения некоторых полей - должна быть только краткая информация об owner.

В данном тесте была так же задана переменная *{{post_id}}* - id вновь созданного пользователя - для использования её в последующих запросах.

```javascript
pm.collectionVariables.set("post_id", jsonData.id)
```

![Ответы для запроса CreatePost_1](https://i.imgur.com/uGX10T7.jpeg)  
![Ответы для запроса CreatePost_2](https://i.imgur.com/rYfHQb5.jpeg)

### GET /post/:id (Get Post Data By Id)

Создано 20 тестов с проверкой соотвествия заданных данных из запроса CREATE Post и данных полученных из тела ответа. Здесь уже использеутся переменная *{{post_id}}* для получения информации о созданном в предыдущем запросе пользователе.

![Ответы для запроса GetPostById_1](https://i.imgur.com/fcgD1Pi.jpeg)
![Ответы для запроса GetPostById_2](https://i.imgur.com/uYv7r96.jpeg)


