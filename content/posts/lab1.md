---
title: "Работа с Git"
date: 2025-09-27
---

# Ход выполнения работы

1. **Создание репозитория**

Создана новая папка, находящаяся на рабочем столе, переходим в нее:
> cd Desktop/demo-repo

Инициализируем локальный репозиторий Git и проверяем его статус:
> git init  
> git status

![git status](https://shamis-08.github.io/hugo-portfolio/images/git/git_status.png)

2. **Создание первого файла и первого коммита**

Создаем файл `file1.md`:
> touch file1.md

Проверяем статус репозитория:
> git status

![status after file1](https://shamis-08.github.io/hugo-portfolio/images/git/git_status_after_file1.png)

Добавляем файл в индекс:
> git add file1.md

Проверяем статус:
> git status

![status after add](https://shamis-08.github.io/hugo-portfolio/images/git/git_status_after_add.png)

Создаем первый коммит:
> git commit -m "Initial commit"

![initial commit](https://shamis-08.github.io/hugo-portfolio/images/git/initial_commit.png)

3. **Просмотр истории коммитов**

Смотрим историю коммитов:
> git log

![git log](https://shamis-08.github.io/hugo-portfolio/images/git/git_log.png)

4. **Создание ветки и работа с ней**

Создаем новую ветку `feature` и переключаемся на нее:
> git checkout -b feature

Проверяем список веток:
> git branch

![git branch](https://shamis-08.github.io/hugo-portfolio/images/git/git_branch.png)

5. **Внесение изменений в ветке feature**

Открываем файл `file1.md` и добавляем произвольный текст:
> nano file1.md

![nano](https://shamis-08.github.io/hugo-portfolio/images/git/nano.png)

Проверяем статус:
> git status

![status after edit](https://shamis-08.github.io/hugo-portfolio/images/git/git_status_after_edit.png)

Добавляем изменения в индекс и создаем коммит:
> git add file1.md  
> git commit -m "Update file1 in feature branch"

![feature commit](https://shamis-08.github.io/hugo-portfolio/images/git/feature_commit.png)

6. **Слияние веток**

Переключаемся на основную ветку:
> git checkout main

Выполняем слияние ветки `feature` в основную:
> git merge feature

![merge](https://shamis-08.github.io/hugo-portfolio/images/git/git_merge.png)

7. **Удаление ветки**

Удаляем ветку `feature` после успешного слияния:
> git branch -d feature

Проверяем список веток:
> git branch

![branch after delete](https://shamis-08.github.io/hugo-portfolio/images/git/git_branch_after_delete.png)

8. **Подключение удаленного репозитория**

Добавляем удаленный репозиторий GitHub:
> git remote add origin https://github.com/shamis-08/demo-repo.git

Проверяем список удаленных репозиториев:
> git remote -v

![git remote](https://shamis-08.github.io/hugo-portfolio/images/git/git_remote.png)

9. **Отправка изменений в удаленный репозиторий**

Отправляем коммиты в удаленный репозиторий:
> git push -u origin master

![git push](https://shamis-08.github.io/hugo-portfolio/images/git/git_push.png)

![demo repo](https://shamis-08.github.io/hugo-portfolio/images/git/demo_repo.png)

# Вывод

В ходе выполнения работы были освоены базовые операции Git: создание локального репозитория, добавление файлов в индекс, создание коммитов, работа с ветками, слияние изменений и отправка проекта в удаленный репозиторий GitHub.