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

2. [Майнд-карта](#Майнд-карта)
3. [Тест-кейсы](#Тест-кейсы)
4. [Баг-репорты](#Баг-репорты)
5. [Коллекции POSTMAN](#Коллекции-POSTMAN)
6. [Автотесты](#Автотесты)

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

//Скачать [майнд-карту](https://drive.google.com/file/d/16KTyHrCGwJSK4sO6ePOPvwgIojN8-KJL/view?usp=share_link) в формате *.xmind
Загрузить МК в репозиторий

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

![Майнд-карта объекта User](https://i.imgur.com/OecxjTh.png)

//Скачать [майнд-карту](https://drive.google.com/file/d/16KTyHrCGwJSK4sO6ePOPvwgIojN8-KJL/view?usp=share_link) в формате *.xmind
Загрузить МК в репозиторий

