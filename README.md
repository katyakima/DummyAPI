# DummyAPI

Здесь представлено описание тестирования проекта [dummyapi.io](https://dummyapi.io/)

## Оглавление

## Описание проекта

[Dummyapi.io](https://dummyapi.io/) - этот проект представляет собой сервис для тестирования API. Он устроен как социальная сеть с пользователями, постами, тегами и комментариями. Для выполнения запросов необходим app-id, который генерируется автоматически в личном кабинете после регистрации на сайте. Для тестирования  выбраны объекты **Post** и **User**.

### USER
___
#### GET /user - Get List

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
