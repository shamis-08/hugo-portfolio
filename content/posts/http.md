---
title: "Протокол HTTP. Клиент-серверное взаимодействие"
date: 2026-01-11
---

# Отчёт по отправке HTTP-запросов с использованием CLI и Postman

## Ход выполнения работы

## 1. GET-запрос

## 1.1 Telnet

В качестве публичного API выбран Swagger Petstore: https://petstore.swagger.io/  
Для GET-запроса используется endpoint получения питомца по ID.

Подключение к API-серверу по порту 80:

    telnet petstore.swagger.io 80

HTTP-запрос, отправленный вручную после установки соединения (пример: petId=1):

    GET /v2/pet/1 HTTP/1.1
    Host: petstore.swagger.io
    Accept: application/json
    Connection: close

![telnet get petstore](https://shamis-08.github.io/hugo-portfolio/images/http/telnet_get_petstore.png)

При выполнении GET-запроса к API Swagger Petstore с использованием Telnet по протоколу HTTP (порт 80) был получен ответ сервера со статус-кодом 302 Moved Temporarily. В заголовке ответа присутствовало поле Location, указывающее на перенаправление запроса на HTTPS-версию ресурса (https://petstore.swagger.io:443/v2/pet/1). Это означает, что сервер настроен на принудительное использование защищённого протокола HTTPS для доступа к API.

Инструменты Telnet и netcat не поддерживают TLS-шифрование и не позволяют напрямую выполнять HTTPS-запросы, поэтому успешное получение данных по данному endpoint через них невозможно. 

## 1.2 cURL

Для получения корректного ответа API был использован инструмент cURL, который поддерживает HTTPS и автоматическое следование редиректам. При выполнении GET-запроса по HTTPS был получен успешный ответ сервера с кодом 200 OK и телом ответа в формате JSON.

Команда:

    curl -i "https://petstore.swagger.io/v2/pet/1"

![curl get petstore](https://shamis-08.github.io/hugo-portfolio/images/http/curl_get_petstore.png)

## 2. POST-запрос

## 2.1 Telnet

Для POST-запроса используется endpoint создания/обновления питомца: `POST /v2/pet`.  
Подключение к API-серверу по порту 80:

    nc petstore.swagger.io 80

Тело запроса: JSON-описание питомца. Для корректного `Content-Length` удобно сначала подготовить JSON одной строкой.

Пример JSON (одной строкой):
    {"id":987654,"name":"ArtemPet","photoUrls":["https://example.com/pet.png"],"status":"available"}

POST-запрос:

    POST /v2/pet HTTP/1.1
    Host: petstore.swagger.io
    Content-Type: application/json
    Accept: application/json
    Content-Length: 94
    Connection: close

    {"id":987654,"name":"ArtemPet","photoUrls":["https://example.com/pet.png"],"status":"available"}

При выполнении POST-запроса к API Swagger Petstore с использованием netcat по протоколу HTTP (порт 80) сервер вернул ответ со статус-кодом 302 Moved Temporarily. В заголовке Location указано перенаправление на HTTPS-версию endpoint (https://petstore.swagger.io:443/v2/pet).

Это свидетельствует о том, что API Swagger Petstore принимает POST-запросы исключительно по защищённому протоколу HTTPS. Инструменты netcat и telnet не поддерживают TLS-шифрование и не позволяют выполнять HTTPS-запросы напрямую, поэтому получение успешного ответа при использовании данных инструментов невозможно.

![netcat post petstore](https://shamis-08.github.io/hugo-portfolio/images/git/netcat_post_petstore.png)

## 2.2 cURL

Для корректного выполнения POST-запроса был использован инструмент cURL, поддерживающий HTTPS и передачу JSON-данных.

Команда:

    curl -i -X POST "https://petstore.swagger.io/v2/pet" \
      -H "Content-Type: application/json" \
      -H "Accept: application/json" \
      -d '{"id":987654,"name":"ArtemPet","photoUrls":["https://example.com/pet.png"],"status":"available"}'

Результат: получен HTTP-ответ с JSON созданногопитомца.

<!-- Скриншот: вывод curl POST (с ключом -i, чтобы был статус-код) -->
![curl post petstore](https://shamis-08.github.io/hugo-portfolio/images/git/curl_post_petstore.png)

## 3. Установка Postman

Postman установлен и успешно запущен

![postman main](https://shamis-08.github.io/hugo-portfolio/images/git/postman_main.png)

## 4. GET-запрос к API Банка России в Postman

Использовано XML API Банка России для получения курса доллара США за период с 01.01.2025 по 10.01.2025.  
Код валюты USD (VAL_NM_RQ): R01235.

URL запроса:

    https://www.cbr.ru/scripts/XML_dynamic.asp?date_req1=01/01/2025&date_req2=10/01/2025&VAL_NM_RQ=R01235

Параметры запроса:
- date_req1 — начальная дата периода  
- date_req2 — конечная дата периода  
- VAL_NM_RQ — код валюты (USD = R01235)  

Тип запроса: GET.

Результат: получен XML-ответ с курсами валют по датам.

![postman cbr request](https://shamis-08.github.io/hugo-portfolio/images/git/postman_cbr.png)

## Вывод
В ходе лабораторной работы выполнены GET- и POST-запросы к публичному Swagger Petstore API с использованием Telnet, netcat и cURL. В Postman выполнен GET-запрос к API Банка России для получения курса выбранной валюты за заданный период.