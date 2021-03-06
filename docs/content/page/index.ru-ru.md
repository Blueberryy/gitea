---
date: "2016-11-08T16:00:00+02:00"
title: "Документация"
slug: "documentation"
url: "/ru-ru/"
weight: 10
toc: true
draft: false
---

# Что такое Gitea?

Удобный сервис собственного хостинга репозиториев Git. Он похож на GitHub, Bitbucket и GitLab..
Gitea это форк [Gogs](http://gogs.io). Ознакомьтесь с [Анонсом Gitea](https://blog.gitea.io/2016/12/welcome-to-gitea/)
сообщением в блоге, чтобы прочитать об обосновании форка.

## Цели

Цель этого проекта - предоставить самый простой, быстрый и самый
удобный сервис собственного хостинга службы Git. С Go это можно сделать с помощью независимого двоичного распределения.
на всех платформах и архитектурах, поддерживаемых Go. Эта поддержка включает Linux, macOS и
Windows, на таких архитектурах, как amd64, i386, ARM, PowerPC и др.

## Особенности

- Панель управления
    - Переключатель контекста (организация или текущий пользователь)
    - График активности
        - Коммиты
        - Задачи
        - Pull request'ы
        - Создание репозитория
    - Список репозиториев с возможностью поиска
    - Список организаций
    - Список зеркальных репозиториев
- Панель управления задачами
    - Переключатель контекста (организация или текущий пользователь)
    - Фильтр по
        - Открытым
        - Закрытым
        - Ваши репозитории
        - Назначенные вам
        - Ваши задачи
        - Репозиторию
    - Сортировка по
        - Старейшим
        - Последнему обновлению
        - Количеству комментариев
- Панель управления Pull request'ом
    - То же, что и панель задач
- Типы репозиториев
    - Зеркальный
    - Обычный
    - Мигрировавший
- Уведомления (электронная почта и онлайн)
    - Прочитанные
    - Непрочитанные
    - Закреплённые
- Страница поиска
    - Пользователей
    - Репозиториев
    - Организаций
    - Поиска
- Пользовательские шаблоны
- Переопредение общедоступных файлов (logo, css, и т.д.)
- Защита CSRF и XSS
- Поддержка HTTPS
- Установите разрешённые размеры и типы загрузки
- Журнал с записями
- Настройка
    - Базы данных
        - MySQL
        - PostgreSQL
        - SQLite3
        - MSSQL
        - TiDB (экспериментальная, не рекомендуется)
    - Файл по настройке сайта
        - [app.ini](https://github.com/go-gitea/gitea/blob/master/custom/conf/app.example.ini)
    - Панель администратора
        - Статистика
        - Действия
            - Удаление неактивных аккаунтов
            - Удаление архивов кешированного репозитория
            - Удаление записей репозиториев, в которых отсутствуют файлы
            - Запуск сборки мусора в репозиториях
            - Переписывание SSH ключей
            - Повторная синхронизация hook'ов
            - Восстановление репозиториев, которые отсутствуют
        - Статус сервера
            - Время работы
            - Память
            - Текущий # goroutine'ов
            - И т.д.
         - Управление пользователями
            - Поиск
            - Сортировка
            - Последний вход в систему
            - Источник аутентификации
            - Максимальное количество репозиториев
            - Отключить учётную запись
            - Права администратора
            - Разрешение на создание hook'ов git
            - Разрешение на создание организаций
            - Разрешение на импорт репозиториев
        - Управление организацией
            - Люди
            - Команды
            - Аватар
            - Hook'и
        - Управление репозиторием
            - Просмотр всей информации о репозиториях и управление репозиториями
        - Источники аутентификации
            - OAuth
            - PAM
            - LDAP
            - SMTP
        - Средство просмотра настройки
            - Всё в файле настройки
        - Системные уведомления
            - Переодические события
        - Мониторинг
            - Текущего процесса
            - Cron jobs
                - Обновление зеркал
                - Проверка работоспособности репозитория
                - Проверить статистику репозитория
                - Очистить старые архивы
    - Переменные окружающей среды
    - Параметры командной строки
- Поддержка многих языков ([21 язык](https://github.com/go-gitea/gitea/tree/master/options/locale))
- Мерами поддерживает и схематическое представление данных, не только гистограммы/диаграммы [Mermaid](https://mermaidjs.github.io/)
- Почтовый сервис
    - Уведомления
    - Подтверждение регистрации
    - Восстановление пароля
- Поддержка обратного прокси(proxy)
    - Включает подпути
- Пользователи
    - Профиль
        - Имя
        - Имя пользователя
        - Эл. почта
        - Веб-сайт
        - Дата регистрации
        - Подпищики и подписки
        - Организации
        - Репозитории
        - Активность
        - Избранные репозитории
    - Настройки
        - То же, что и профиль, и многое другое ниже
        - Держите электронную почту скрытой
        - Аватар
            - Gravatar
            - Libravatar
            - Пользовательский
        - Пароль
        - Несколько адресов электронной почты
        - SSH ключи
        - Подключенные приложения
        - Двухфакторная аутентификация
        - Привязанные источники OAuth2
        - Удалить аккаунт
- Репозитории
    - Клонировать с помощью SSH/HTTP/HTTPS
    - Git LFS
    - Отслеживание, Избранное, Форк
    - Просмотр отслеживающих, звездочетов и форк
    - Код
        - Просмотр веток
        - Загрузка и создание файлов через Интернет
        - Клонирование url
        - Скачивание
            - ZIP
            - TAR.GZ
        - Веб-редактор
            - Редактор Markdown
            - Текстовый редактор
                - Подсветка синтаксиса
            - Предпросмотр Diff(списка изменений)
            - Предпросмотр
            - Выберите, куда загрузить коммит
        - Просмотр истории файлов
        - Удаление файла
        - Просмотр исходника
    - Задачи
        - Шаблоны задач
        - Этапы
        - Метки
        - Назначение задач
        - Отслеживание времени
        - Реакции
        - Фильтр
            - Открытые
            - Закрытые
            - Назначение кому-то
            - Созданные вами
            - Упомянуты вы
        - Сортировка
            - По дате
            - Последнему обновлению
            - Количество комментариев
        - Поиск
        - Комментарии
        - Прикрепление файлов
    - Pull request'ы
        - Те же функции, что в задачах
    - Коммиты
        - График коммитов
        - Коммиты по ветке
        - Поиск
        - Поиск во всех ветках
        - Показать diff(изменения)
        - Показать SHA
        - Показать автора
        - Просмотр файлов в коммите
    - Релизы
        - Прикрепление файлов
        - Название
        - Содержание
        - Удаление
        - Отметить как pre-release
        - Выбор ветки
    - Вики
        - Импорт
        - Редактор Markdown
    - Настройки
        - Настройки
            - Название
            - Описание
            - Приватный/общедоступный
            - Веб-сайт
            - Вики
                - Включено/выключено
                - Внутренний/внешний
            - Задачи
                - Включено/выключено
                - Внутренний/внешний
                - Внешний поддерживает переопределение URL-адресов для лучшей интеграции
            - Включение/отключение запросов на pull request
            - Передать права собственности
            - Удаление вики
            - Удаление репозитория
        - Соавторы
            - Чтение/запись/админ
        - Ветки
            - Ветка по умолчанию
            - Защита ветки
        - Веб-хуки
        - Git hook'и
        - Ключи развёртывания

## Системные требования

- Raspberry Pi 3 достаточно мощный, чтобы запускать Gitea для небольших рабочих нагрузок.
- 2 ядра ЦП и 1 ГБ ОЗУ обычно достаточно для небольших команд/проектов..
- Gitea следует запускать с выделенной системной учётной записью без прав root в системах типа UNIX.
   - Примечание: Gitea управляет файлом `~/.ssh/authorized_keys`. Запуск Gitea от имени обычного пользователя может помешать этому пользователю войти в систему.
- [Git](https://git-scm.com/) версии 1.7.2 или лучше требуется. Версия 1.9.0 или более поздней версии. Также обратите внимание:
   - Git [большое файловое хранилище](https://git-lfs.github.com/) будет доступен, если включен, когда git >= 2.1.2.
   - Git рендеринг коммит-графа будет включен автоматически, когда git >= 2.18.

## Поддержка браузера

- Последние 2 версии Chrome, Firefox, Safari, Edge (EdgeHTML) и Edge (Chromium)
- Firefox ESR

## Компоненты

* Веб-фреймворк: [Macaron](http://go-macaron.com/)
* ORM: [XORM](https://github.com/go-xorm/xorm)
* Компоненты пользовательского интерфейса:
  * [Semantic UI](http://semantic-ui.com/)
  * [GitHub Octicons](https://octicons.github.com/)
  * [Font Awesome](http://fontawesome.io/)
  * [DropzoneJS](http://www.dropzonejs.com/)
  * [Highlight](https://highlightjs.org/)
  * [Clipboard](https://zenorocha.github.io/clipboard.js/)
  * [CodeMirror](https://codemirror.net/)
  * [jQuery MiniColors](https://github.com/claviska/jquery-minicolors)
* Драйверы базы данных:
  * [github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql)
  * [github.com/lib/pq](https://github.com/lib/pq)
  * [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3)
  * [github.com/pingcap/tidb](https://github.com/pingcap/tidb)
  * [github.com/denisenkom/go-mssqldb](https://github.com/denisenkom/go-mssqldb)

## Программное обеспечение и сервисная поддержка

- [Drone](https://github.com/drone/drone) (CI)
