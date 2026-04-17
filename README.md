# Лабораторная работа: Разработка REST API на ASP.NET Core

## Основная информация
**ФИО:** Микаилов Ахмед
**Группа:** ИСП-231
**Дата:** 17.04ю2026

## Краткое описание работы
В ходе лабораторной работы изучены основы создания REST API с использованием ASP.NET Core Controllers. Реализованы CRUD операции, фильтрация, поиск, сортировка и получение статистики по задачам. Освоены маршрутизация, работа с DTO, HTTP статусы и CORS.

## Структура проекта
TaskApi/
├── Controllers/
│ └── TasksController.cs
├── Models/
│ ├── TaskItem.cs
│ ├── CreateTaskDto.cs
│ └── UpdateTaskDto.cs
├── Program.cs
└── appsettings.json

text

## Список реализованных маршрутов

| Метод | Маршрут | Описание |
|-------|---------|----------|
| GET | /api/tasks | Получить все задачи |
| GET | /api/tasks?completed={bool} | Фильтрация по статусу |
| GET | /api/tasks/{id} | Получить задачу по id |
| GET | /api/tasks/search?query={string} | Поиск по заголовку и описанию |
| GET | /api/tasks/priority/{level} | Фильтрация по приоритету |
| GET | /api/tasks/stats | Получить статистику |
| GET | /api/tasks/sorted?by={field}&desc={bool} | Сортировка |
| POST | /api/tasks | Создать новую задачу |
| PUT | /api/tasks/{id} | Полное обновление задачи |
| PATCH | /api/tasks/{id}/complete | Переключить статус |
| DELETE | /api/tasks/{id} | Удалить задачу |

## Итоговая таблица ASP.NET Core Controller-based API

| Аспект | ASP.NET Core Controllers |
|--------|--------------------------|
| Маршруты | [HttpGet] атрибут над методом |
| Группировка маршрутов | Класс-контроллер |
| Базовый URL | [Route("api/[controller]")] |
| Параметр пути | (int id) — параметр метода |
| Параметр запроса | [FromQuery] bool? completed |
| Тело запроса | [FromBody] CreateTaskDto dto |
| Ответ 200 | return Ok(data) |
| Ответ 201 | return CreatedAtAction(...) |
| Ответ 404 | return NotFound(...) |
| Ответ 204 | return NoContent() |
| Типизация данных | Строгая (C#) |
| Документация | Swagger — устанавливается отдельно |

## Главные выводы

1. REST — не протокол, а архитектурный стиль. Те же принципы работают с любым языком и фреймворком.

2. Контроллер в ASP.NET Core = Router в Express, только с автоматической документацией и строгой типизацией.

3. DTO защищает API от некорректных данных: клиент передаёт только то, что сервер разрешает принять.

4. Swagger UI позволяет тестировать API без Postman и без написания тестового JavaScript-кода.

5. Правильные HTTP-статусы — часть «контракта» API. Клиент должен понимать, что произошло, по коду ответа.