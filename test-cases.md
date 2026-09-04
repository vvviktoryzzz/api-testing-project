# Test Cases — JSONPlaceholder API

## TC-API-001 — Get all posts

**Method:** GET  
**Endpoint:** `/posts`

**Preconditions:**
- API is available

**Steps:**
1. Send GET request to `/posts`.

**Expected result:**
- Response status is `200 OK`.
- Response contains an array of posts.
- Each post contains `userId`, `id`, `title` and `body`.

**Actual result:**
- Response status is `200 OK`.
- Array of posts is returned.
- Post objects contain the expected fields.

**Status:** PASS

---

## TC-API-002 — Get post by ID

**Method:** GET  
**Endpoint:** `/posts/1`

**Steps:**
1. Send GET request to `/posts/1`.

**Expected result:**
- Response status is `200 OK`.
- One post is returned.
- Post ID is `1`.

**Actual result:**
- Response status is `200 OK`.
- One post with ID `1` is returned.

**Status:** PASS

---

## TC-API-003 — Get non-existing post

**Method:** GET  
**Endpoint:** `/posts/999`

**Steps:**
1. Send GET request to `/posts/999`.

**Expected result:**
- Response status is `404 Not Found`.
- Non-existing post is not returned.

**Actual result:**
- Response status is `404 Not Found`.

**Status:** PASS

---

## TC-API-004 — Create post with valid data

**Method:** POST  
**Endpoint:** `/posts`

**Request body:**

```json
{
  "title": "QA test post",
  "body": "This post was created during API testing",
  "userId": 1
}
