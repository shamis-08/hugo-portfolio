---
title: "Vue 3. Практическое задание"
date: 2026-01-06
---

# Отчет по разработке SPA-приложения на Vue 3 с сервером на Python

Ссылка на GitHub:
- https://github.com/shamis-08/taskManager_vue3

## 1. Цель работы

Разработать учебное веб-приложение **Task Manager** на базе:

- **Frontend:** Vue 3 (Composition API, Vue Router)
- **Backend:** FastAPI (Python)
- **Хранение:** JSON-файл
- **Сборка:** Docker

Приложение должно реализовывать CRUD-операции над задачами, поддержку маршрутов, формы с валидацией и работу с REST API.

## 3. Реализованный функционал

### 3.1. Созданные компоненты

| Компонент | Назначение |
|-----------|------------|
| **AppHeader.vue** | шапка приложения, навигация |
| **AppFooter.vue** | нижняя панель |
| **LayoutCard.vue** | layout-контейнер со слотами |
| **TaskList.vue** | список задач |
| **TaskItem.vue** | отдельная задача |
| **TaskForm.vue** | форма создания/редактирования |
| **TasksView.vue** | страница управления задачами |
| **TaskCreateView.vue** | создание задачи |
| **TaskEditView.vue** | редактирование задачи |
| **HomeView.vue** | главная страница |
| **NotFoundView.vue** | страница 404 |

---

### 3.2. computed / watch

- **computed** — для фильтрации и сортировки:

```js
const filteredTasks = computed(() =>
  tasks.value.filter(t =>
    filterStatus.value === 'completed' ? t.completed :
    filterStatus.value === 'active' ? !t.completed : true
  )
)

const sortedTasks = computed(() => {
  const copy = [...filteredTasks.value]
  return sortBy.value === 'title'
    ? copy.sort((a, b) => a.title.localeCompare(b.title))
    : copy.sort((a, b) => new Date(a.created_at) - new Date(b.created_at))
})
```

- **watch** — отслеживание изменения фильтра:

```js
watch(filterStatus, value => {
  console.log('Фильтр изменился:', value)
})
```

### 3.3. Использование слотов

Компонент **LayoutCard.vue** содержит:

- обычный слот  
- именованные слоты `header` и `footer`  
- scoped-slot с параметром `padding`

```vue
<slot :padding="16">
  <p>Нет содержимого</p>
</slot>
```

### 3.4. Маршруты приложения

| Маршрут | Назначение |
|--------|------------|
| `/` | главная страница |
| `/tasks` | список задач |
| `/tasks/new` | создание задачи |
| `/tasks/:id/edit` | редактирование задачи |
| `/:pathMatch(.*)*` | страница 404 |

Реализованы вложенные и именованные маршруты, программная навигация и страница 404.

### 3.5. Серверная часть

Сервер реализован на **FastAPI**.

Поддерживаемые эндпоинты:

- GET /api/tasks
- GET /api/tasks/{id}
- POST /api/tasks
- PUT /api/tasks/{id}
- DELETE /api/tasks/{id}

Данные хранятся в файле **tasks.json**

## 4. Скриншоты интерфейса

**Главная**
![Главная](https://shamis-08.github.io/hugo-portfolio/images/task_manager/home.png)
**Список задач**
![Список задач](https://shamis-08.github.io/hugo-portfolio/images/task_manager/tasks.png)
**Фильтрация по статусу**
![Фильтрация](https://shamis-08.github.io/hugo-portfolio/images/task_manager/filter.png)
**Сортировка по названию**
![Сортировка](https://shamis-08.github.io/hugo-portfolio/images/task_manager/sort.png)
**Создание**
![Создание](https://shamis-08.github.io/hugo-portfolio/images/task_manager/create.png)
**Редактирование**
![Редактирование](https://shamis-08.github.io/hugo-portfolio/images/task_manager/edit.png)
**404**
![404](https://shamis-08.github.io/hugo-portfolio/images/task_manager/404.png)

## 5. Пример кода

```vue
<TaskItem
  v-for="task in sortedTasks"
  :key="task.id"
  :task="task"
  @delete="deleteTask"
  @toggle="toggleTask"
/>
```

## 6. Пример данных (JSON)

```json
[
  {
    "title": "Название задачи",
    "description": "описание задачи",
    "priority": "high",
    "category": "study",
    "is_important": true,
    "completed": false,
    "id": 1,
    "created_at": "2026-01-01T18:00:00.000000"
  }
]
```

## 7. Инструкция по запуску (Docker)

```bash
docker compose build
docker compose up
```

После запуска:

- backend — http://localhost:8000  
- frontend — http://localhost:5173

## 8. Выводы

В ходе выполнения работы были изучены:

- структура и синтаксис **Vue 3**
- компонентный подход
- **Vue Router** и SPA-маршрутизация
- работа с формами и `v-model`
- взаимодействие с REST API
- реализация backend на **FastAPI**
- контейнеризация приложений с **Docker**
- организация файловой структуры SPA-проекта