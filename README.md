# API Testing — REST API

Учебный QA-проект по функциональному тестированию REST API с использованием Postman.

## Цель проекта

Проверить корректность работы REST API при выполнении основных HTTP-запросов, обработку валидных и невалидных данных, HTTP status codes и структуру JSON-ответов.

## API

Для тестирования используется публичный mock API **JSONPlaceholder**.

Основной endpoint:

`https://jsonplaceholder.typicode.com/posts`

## Что тестировалось

* GET — получение списка ресурсов
* GET — получение конкретного ресурса
* GET — обработка запроса к несуществующему ресурсу
* POST — создание нового ресурса
* POST — обработка запроса без обязательного поля
* PUT — полное обновление ресурса
* PATCH — частичное обновление ресурса
* DELETE — удаление ресурса
* HTTP status codes
* Response body
* JSON structure
* Валидация входных данных
* Positive / Negative scenarios

## Postman Requests

В Postman Collection содержится **8 API-запросов**:

* GET — Get all posts
* GET — Get post by ID
* GET — Get non-existing post
* POST — Create post
* POST — Create post without title
* PUT — Update post
* PATCH — Update post title
* DELETE — Delete post

## Результаты тестирования

Всего создано **10 test cases**:

* **9 PASS**
* **1 FAIL**

Неуспешная проверка связана с валидацией обязательного поля `title`. JSONPlaceholder принимает POST-запрос без этого поля и возвращает `201 Created`.

Так как JSONPlaceholder является mock API и не реализует строгую валидацию данных, результат зафиксирован как **validation issue / API limitation**, а не как подтверждённый production bug.

## Артефакты тестирования

* [Checklist](checklist.md)
* [Test Cases](test-cases.md)
* [Postman Collection](postman/collection.json)

## Использованные подходы

* API Testing
* Functional Testing
* Positive / Negative Testing
* Validation Testing
* Status Code Validation
* Response Validation

## Tools

* Postman
* Git
* GitHub

## Project Structure

```text
api-testing-project/
├── README.md
├── checklist.md
├── test-cases.md
└── postman/
    └── collection.json
```
