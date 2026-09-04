# Test Cases — JSONPlaceholder API

## TC-API-001 — Get all posts

**Метод:** GET
**Endpoint:** `/posts`

**Предусловия:**

* API доступен.

**Шаги:**

1. Отправить GET-запрос на `/posts`.

**Ожидаемый результат:**

* HTTP status code — `200 OK`.
* В response возвращается массив posts.
* Каждый post содержит поля `userId`, `id`, `title` и `body`.

**Фактический результат:**

* HTTP status code — `200 OK`.
* Возвращается массив posts.
* Объекты posts содержат ожидаемые поля.

**Статус:** PASS

---

## TC-API-002 — Get post by ID

**Метод:** GET
**Endpoint:** `/posts/1`

**Шаги:**

1. Отправить GET-запрос на `/posts/1`.

**Ожидаемый результат:**

* HTTP status code — `200 OK`.
* Возвращается один post.
* ID post равен `1`.

**Фактический результат:**

* HTTP status code — `200 OK`.
* Возвращается один post с ID `1`.

**Статус:** PASS

---

## TC-API-003 — Get non-existing post

**Метод:** GET
**Endpoint:** `/posts/999`

**Шаги:**

1. Отправить GET-запрос на `/posts/999`.

**Ожидаемый результат:**

* HTTP status code — `404 Not Found`.
* Несуществующий post не возвращается.

**Фактический результат:**

* HTTP status code — `404 Not Found`.

**Статус:** PASS

---

## TC-API-004 — Create post with valid data

**Метод:** POST
**Endpoint:** `/posts`

**Request body:**

```json
{
  "title": "QA test post",
  "body": "This post was created during API testing",
  "userId": 1
}
```

**Шаги:**

1. Отправить POST-запрос с валидными данными.

**Ожидаемый результат:**

* HTTP status code — `201 Created`.
* В response возвращаются переданные данные.
* Созданному post присваивается ID.

**Фактический результат:**

* HTTP status code — `201 Created`.
* Переданные данные возвращаются в response.
* Созданному post присвоен ID `101`.

**Статус:** PASS

---

## TC-API-005 — Create post without title

**Метод:** POST
**Endpoint:** `/posts`

**Request body:**

```json
{
  "body": "This post has no title",
  "userId": 1
}
```

**Шаги:**

1. Отправить POST-запрос без обязательного поля `title`.

**Ожидаемый результат:**

* API отклоняет запрос, так как отсутствует обязательное поле `title`.
* Возвращается ошибка валидации.

**Фактический результат:**

* HTTP status code — `201 Created`.
* Post принимается без поля `title`.

**Статус:** FAIL

**Примечание:**

JSONPlaceholder является mock API и не реализует строгую валидацию обязательных полей. Поэтому данный результат зафиксирован как неуспешная проверка валидации, а не как подтверждённый production bug.

---

## TC-API-006 — Update post using PUT

**Метод:** PUT
**Endpoint:** `/posts/1`

**Request body:**

```json
{
  "id": 1,
  "title": "Updated QA test post",
  "body": "This post was updated during API testing",
  "userId": 1
}
```

**Шаги:**

1. Отправить PUT-запрос с полными обновлёнными данными post.

**Ожидаемый результат:**

* HTTP status code — `200 OK`.
* В response возвращается обновлённый post.
* Все переданные поля содержат обновлённые значения.

**Фактический результат:**

* HTTP status code — `200 OK`.
* В response возвращается обновлённый post с переданными значениями.

**Статус:** PASS

---

## TC-API-007 — Update post title using PATCH

**Метод:** PATCH
**Endpoint:** `/posts/1`

**Request body:**

```json
{
  "title": "PATCH updated title"
}
```

**Шаги:**

1. Отправить PATCH-запрос, передав только поле `title`.

**Ожидаемый результат:**

* HTTP status code — `200 OK`.
* Значение `title` изменено.
* Остальные поля остаются без изменений.

**Фактический результат:**

* HTTP status code — `200 OK`.
* Значение `title` изменено.
* Поля `userId` и `body` остались без изменений.

**Статус:** PASS

---

## TC-API-008 — Delete post

**Метод:** DELETE
**Endpoint:** `/posts/1`

**Шаги:**

1. Отправить DELETE-запрос на `/posts/1`.

**Ожидаемый результат:**

* HTTP status code — `200 OK`.
* Запрос на удаление обработан успешно.

**Фактический результат:**

* HTTP status code — `200 OK`.
* Запрос обработан успешно.

**Статус:** PASS

---

## TC-API-009 — Validate response JSON structure

**Метод:** GET
**Endpoint:** `/posts/1`

**Шаги:**

1. Отправить GET-запрос на `/posts/1`.
2. Проверить структуру response body.

**Ожидаемый результат:**

* Response содержит корректный JSON.
* Response содержит следующие поля:

  * `userId`
  * `id`
  * `title`
  * `body`

**Фактический результат:**

* Response содержит корректный JSON.
* Все ожидаемые поля присутствуют.

**Статус:** PASS

---

## TC-API-010 — Validate HTTP status codes

**Проверяемые запросы:**

1. GET `/posts`
2. GET `/posts/999`
3. POST `/posts`
4. PUT `/posts/1`
5. PATCH `/posts/1`
6. DELETE `/posts/1`

**Ожидаемый результат:**

| HTTP method | Scenario                          | Expected status code |
| ----------- | --------------------------------- | -------------------- |
| GET         | Получение существующего ресурса   | `200 OK`             |
| GET         | Получение несуществующего ресурса | `404 Not Found`      |
| POST        | Создание ресурса                  | `201 Created`        |
| PUT         | Полное обновление ресурса         | `200 OK`             |
| PATCH       | Частичное обновление ресурса      | `200 OK`             |
| DELETE      | Удаление ресурса                  | `200 OK`             |

**Фактический результат:**

* Все полученные HTTP status codes соответствуют ожидаемым значениям.

**Статус:** PASS
