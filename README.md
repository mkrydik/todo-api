# ToDo API

- Ruby : `ruby 3.2.0 (2022-12-25 revision a528908271) [x86_64-linux]`
- SQLite3 : `3.46.1 2024-08-13 09:16:08 c9c2ab54ba1f5f46360f1b4f35d849cd3f080e6fc2b6c60e91b16c63f69a1e33 (64-bit)`
- Dev Server : `$ bin/rails server`

```bash
$ rails new todo-api --api --minimal
$ cd ./todo-api/
$ bin/rails g scaffold Todo content:string
$ bin/rails db:migrate
$ bin/rails s
```

```bash
$ curl -sS -X POST -H 'Content-Type: application/json' -d '{ "todo": { "content": "Test 1" } }' http://localhost:3000/todos | jq '.'
{
  "id": 1,
  "content": "Test 1",
  "created_at": "2024-10-12T10:43:50.302Z",
  "updated_at": "2024-10-12T10:43:59.671Z"
}

$ curl -sS -X PUT -H 'Content-Type: application/json' -d '{ "todo": { "content": "Test 2" } }' http://localhost:3000/todos/1 | jq '.'
{
  "id": 1,
  "content": "Test 2",
  "created_at": "2024-10-12T10:43:50.302Z",
  "updated_at": "2024-10-12T10:44:51.768Z"
}

$ curl -sS http://localhost:3000/todos | jq '.'
[
  {
    "id": 1,
    "content": "Test 2",
    "created_at": "2024-10-12T10:43:50.302Z",
    "updated_at": "2024-10-12T10:44:51.768Z"
  }
]

$ curl -sS -X DELETE -H 'Content-Type: application/json' http://localhost:3000/todos/1 | jq '.'
```
