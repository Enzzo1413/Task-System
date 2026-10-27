# To-Do System (CodeIgniter 4)

The web part of the project. It has **no database of its own** - every task is
stored by the separate **Task API** (folder `task-api`, the only thing that gets hosted).

## Structure
```
app/Controllers/Home.php            "/" -> redirects to /tasks
app/Controllers/Tasks.php           pages: list + filter, add, edit, done/undo, delete
app/Libraries/TaskApiClient.php     calls the hosted API (list, get, create, update, delete)
app/Config/TaskApi.php              API URL + key (can be set in .env)
app/Views/tasks/index.php           task list with filter bar
app/Views/tasks/form.php            add / edit form
app/Config/Routes.php               / and /tasks routes
```

## Run it
1. Host the API first (see `../task-api/README.md`) and note its URL.
2. In `.env`, set `taskapi.baseUrl` (the API URL) and `taskapi.apiKey` (any secret, 6+ characters).
3. In this folder:
   ```
   composer install      # only if the vendor/ folder is missing
   php spark serve
   ```
4. Open http://localhost:8080 - adding a task here saves it through the hosted API.

Requires PHP 8.2+ with the curl extension.
