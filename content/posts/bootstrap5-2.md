---
title: "Интеграция Bootstrap 5 в приложение с luxon. Этап 2"
date: 2026-01-06
---

Ссылка на helios:
- https://se.ifmo.ru/~s369039/bootstrap5-2/

## Внешний вид приложения с открытым окном

![bootstrap5-2](https://shamis-08.github.io/hugo-portfolio/images/bootstrap5-2.png)

## Код

```html
<!doctype html>
<html lang="ru">
<head>
    <meta charset="utf-8">
    <title>Продукт — Одностраничный сайт на Bootstrap 5</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <link
            href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
            rel="stylesheet"
    >

    <link
            rel="stylesheet"
            href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css"
    >
</head>
<body class="d-flex flex-column min-vh-100">

<!-- Навбар -->
<nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
        <a class="navbar-brand fw-bold" href="#hero">МойПродукт</a>
        <button class="navbar-toggler" type="button"
                data-bs-toggle="collapse"
                data-bs-target="#mainNavbar"
                aria-controls="mainNavbar"
                aria-expanded="false"
                aria-label="Переключение навигации">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse justify-content-end" id="mainNavbar">
            <ul class="navbar-nav">
                <li class="nav-item">
                    <a class="nav-link active" href="#hero">Главная</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#contacts">Контакты</a>
                </li>
            </ul>
        </div>
    </div>
</nav>

<section id="hero" class="bg-light py-5 mt-5">
    <div class="container">
        <div class="row align-items-center">
            <div class="col-lg-8">
                <h1 class="display-4 fw-bold mb-3">Добро пожаловать!</h1>
                <h2 class="h4 text-muted mb-4">
                    Мы помогаем быстро запускать адаптивные сайты и лендинги
                    с использованием Bootstrap 5.
                </h2>

                <p class="lead mb-4">
                    Создайте современный, аккуратный и удобный интерфейс без погружения в
                    сложную верстку с нуля.
                </p>

                <!-- Кнопка открытия формы обратной связи (модальное окно) -->
                <button type="button"
                        class="btn btn-primary btn-lg"
                        data-bs-toggle="modal"
                        data-bs-target="#contactModal">
                    Связаться с нами
                </button>
            </div>
        </div>
    </div>
</section>

<!-- Блок с luxon: 3 колонки 2-8-2 -->
<section class="py-4">
    <div class="container">
        <div class="row align-items-center">
            <div class="col-12 col-md-2">
                <!-- Пустая колонка слева -->
            </div>
            <div class="col-12 col-md-8">
                <button
                        id="showTimeBtn"
                        type="button"
                        class="btn btn-danger btn-lg w-100"
                        data-bs-toggle="modal"
                        data-bs-target="#timeModal">
                    Показать время
                </button>
            </div>
            <div class="col-12 col-md-2">
                <!-- Пустая колонка справа -->
            </div>
        </div>
    </div>
</section>

<section class="py-5">
    <div class="container">
        <h3 class="text-center mb-5 fw-bold">Почему именно наш продукт</h3>
        <div class="row g-4">

            <!-- Блок 1
             на маленьких экранах идет вторым, на больших — первым -->
            <div class="col-md-4 order-2 order-md-1">
                <div class="h-100 p-4 border rounded-3 text-center">
                    <div class="mb-3">
                        <i class="fa-solid fa-bolt fa-2x text-primary"></i>
                    </div>
                    <h4 class="fw-semibold mb-3">Быстрый старт</h4>
                    <p class="mb-0">
                        Используйте готовые компоненты Bootstrap, чтобы запустить сайт
                        за считанные часы, а не дни.
                    </p>
                </div>
            </div>

            <!-- Блок 2
            на маленьких экранах идет первым, на больших — вторым -->
            <div class="col-md-4 order-1 order-md-2">
                <div class="h-100 p-4 border rounded-3 text-center">
                    <div class="mb-3">
                        <i class="fa-solid fa-mobile-screen-button fa-2x text-success"></i>
                    </div>
                    <h4 class="fw-semibold mb-3">Адаптивный дизайн</h4>
                    <p class="mb-0">
                        Сетка Bootstrap и flexbox гарантируют корректное отображение
                        на смартфонах, планшетах и ПК.
                    </p>
                </div>
            </div>

            <!-- Блок 3 -->
            <div class="col-md-4 order-3 order-md-3">
                <div class="h-100 p-4 border rounded-3 text-center">
                    <div class="mb-3">
                        <i class="fa-solid fa-shield-halved fa-2x text-danger"></i>
                    </div>
                    <h4 class="fw-semibold mb-3">Надежность</h4>
                    <p class="mb-0">
                        Проверенный фреймворк, большая документация и сообщество
                        помогают поддерживать проект в отличной форме.
                    </p>
                </div>
            </div>

        </div>
    </div>
</section>

<!-- Модальное окно с формой обратной связи -->
<div class="modal fade" id="contactModal" tabindex="-1" aria-hidden="true">
    <!--
      modal-dialog-centered — вертикальная центровка (flexbox)
      modal-fullscreen-sm-down — на мобильных устройствах форма занимает всю ширину экрана
    -->
    <div class="modal-dialog modal-dialog-centered modal-lg modal-fullscreen-sm-down">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title">Форма обратной связи</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal"
                        aria-label="Закрыть"></button>
            </div>
            <div class="modal-body d-flex justify-content-center">
                <!-- Flex-контейнер, центрируем форму -->
                <form class="w-100">
                    <div class="mb-3">
                        <label for="name" class="form-label">Имя</label>
                        <input type="text"
                               class="form-control"
                               id="name"
                               placeholder="Ваше имя">
                    </div>
                    <div class="mb-3">
                        <label for="email" class="form-label">Email</label>
                        <input type="email"
                               class="form-control"
                               id="email"
                               placeholder="name@example.com">
                    </div>
                    <div class="mb-3">
                        <label for="message" class="form-label">Сообщение</label>
                        <textarea class="form-control"
                                  id="message"
                                  rows="4"
                                  placeholder="Ваше сообщение"></textarea>
                    </div>
                </form>
            </div>
            <div class="modal-footer justify-content-between">
                <span class="text-muted small">
                    Мы ответим в течение 24 часов.
                </span>
                <button type="button" class="btn btn-primary">
                    Отправить
                </button>
            </div>
        </div>
    </div>
</div>

<!-- Модальное окно с luxon-датой/временем -->
<div class="modal fade" id="timeModal" tabindex="-1" aria-hidden="true">
    <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title">Выполнила: Шамис Алена</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal"
                        aria-label="Закрыть"></button>
            </div>
            <div class="modal-body">
                <p id="dateTimeText" class="lead mb-0"></p>
            </div>
            <div class="modal-footer">
                <button type="button"
                        class="btn btn-secondary"
                        data-bs-dismiss="modal">
                    Закрыть
                </button>
            </div>
        </div>
    </div>
</div>

<!--Нижний колонтитул-->
<footer id="contacts" class="bg-dark text-white py-4 mt-auto d-none d-md-block">
    <div class="container">
        <div class="row gy-2">
            <div class="col-md-4">
                <h5 class="h6 text-uppercase fw-bold mb-2">Контакты</h5>
                <p class="mb-1"><i class="fa-solid fa-phone me-2"></i>+7 (900) 123-45-67</p>
                <p class="mb-1"><i class="fa-solid fa-envelope me-2"></i>info@shamis-08.ru</p>
            </div>
            <div class="col-md-4">
                <h5 class="h6 text-uppercase fw-bold mb-2">Адрес</h5>
                <p class="mb-0">
                    <i class="fa-solid fa-location-dot me-2"></i>
                    г. Санкт-Петербург, ул. Ломоносова, д. 9
                </p>
            </div>
            <div class="col-md-4 text-md-end">
                <h5 class="h6 text-uppercase fw-bold mb-2">Мы в сети</h5>
                <a href="#" class="text-white me-3"><i class="fa-brands fa-vk"></i></a>
                <a href="#" class="text-white me-3"><i class="fa-brands fa-telegram"></i></a>
                <a href="#" class="text-white"><i class="fa-brands fa-github"></i></a>
            </div>
        </div>
    </div>
</footer>

<script
        src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js">
</script>

<!-- Luxon -->
<script src="https://cdn.jsdelivr.net/npm/luxon@3/build/global/luxon.min.js"></script>

<!-- Скрипт для вывода даты/времени -->
<script>
    document.addEventListener('DOMContentLoaded', function () {
        const DateTime = luxon.DateTime;
        const showTimeBtn = document.getElementById('showTimeBtn');
        const dateTimeText = document.getElementById('dateTimeText');

        showTimeBtn.addEventListener('click', function () {
            const now = DateTime.now().setLocale('ru');
            const formatted = now.toFormat('dd.MM.yyyy HH:mm:ss');
            dateTimeText.textContent = formatted;
        });
    });
</script>

</body>
</html>
```