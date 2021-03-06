---
date: "2019-11-21T17:00:00-03:00"
title: "Использование: Автоматически связанные ссылки"
slug: "automatically-linked-references"
weight: 15
toc: true
draft: false
menu:
  sidebar:
    parent: "usage"
    name: "Автоматически связанные ссылки"
    weight: 15
    identifier: "automatically-linked-references"
---

# Автоматически связанные ссылки в задачах, Pull Request'ах и сообщениях о фиксации

Когда публикуется задача, Pull Request или комментарий, текстовое
описание анализируется в поиске ссылок. Эти ссылки будут отображаться в виде
ссылок в обзоре задач и, в некоторых случаях, будут давать определённые _действия_.

Аналогичным образом сообщения коммита анализируются, когда они перечислены, и _действия_
могут быть запущены, когда они помещены в основную ветвь.

Чтобы предотвратить создание непреднамеренных ссылок, существуют определённые правила
их распознавания. Например, их нельзя включать в текст кода. Они также должны быть разумно
очищены от окружающего их текста (например, с использованием пробелов).

## Упоминания пользователей, команды и организации

Когда текст в форме `@username` найден и`username`
совпадает с именем существующего пользователя, создаётся
ссылка _mention_. Это будет показано путем преобразования
текста в ссылку на указанный профиль пользователя и, возможно,
создания уведомления для указанного пользователя в зависимости
от того, имеют ли они необходимое разрешение для доступа
к содержимому.

Пример:

> [@Джон](#), можешь ли ты взглянуть на это?

Это также верно для команд и организаций.:

> [@Документеры](#), нам нужно спланировать это.

> [@КрутаяКампанияИнк](#), эта задача касается всех нас!

Команды будут получать уведомления по электронной почте, когда это необходимо, но целые организации - нет.

Сообщения коммитов не производят уведомлений пользователя.

## Коммиты

На коммиты можно ссылаться, используя их хэш SHA1 или его часть длиной не менее
семи символов. Они будут показаны как ссылка на соответствующий коммит.

Пример:

> Эта ошибка появилась в [e59ff077](#)

## Задачи и Pull Request'ы

Ссылка на другую задачу или Pull Request может быть создана с использованием простой
записи `#1234`, где _1234_ - это номер задачи или Pull Request'а в том же репозитории.
Эти ссылки будут показаны как ссылки на указанное содержимое.

Эффект от создания ссылки этого типа заключается в том, что в документе, на который имеется ссылка,
будет создано _уведомление_, при условии, что создатель ссылки имеет права на чтение.

Пример:

> Это похоже относится к [#1234](#)

На задачи и Pull Request'ы в других репозиториях также
можно ссылаться с помощью формы `owner/repository#1234`:

> Это похоже относится к [mike/compiler#1234](#)

В качестве альтернативы также можно использовать обозначение `!1234`. Даже когда
в Gitea Pull Request является формой задачи, форма `#1234` всегда будет ссылаться
на задачу; если связанная запись является Pull Request'ом, Gitea перенаправит его
соответствующим образом. С обозначением `!1234` будет создана ссылка Pull Request'а,
которая при необходимости будет перенаправлена на задачу. Однако это различие может
быть важным, если используется внешний трекер, где ссылки на задачи и Pull Request'ы
не взаимозаменяемы.

## Ссылки на действия в Pull Request'ах и сообщениях коммита

Иногда коммит или Pull Request может исправить или вернуть проблему,
задокументированную в конкретной задаче. Gitea поддерживает закрытие
и повторное открытие задач, на которые имеется ссылка, путем добавления
перед ссылкой определенного _ключевого слова_. Общие ключевые слова включают "закрытие", "исправление", "повторное открытие" и т.д. Этот список может быть
[настроен]({{< ref "/doc/advanced/config-cheat-sheet.ru-ru.md" >}}) посредством
администратор сайта.

Пример:

> Этот PR _закрыт_ [#1234](#)

Если действующая ссылка принята, это создаст уведомление о указанной
задаче, объявляющее, что она будет закрыта, когда ссылающийся PR
будет объединён.

Чтобы ссылка была принята, должно быть выполнено хотя бы одно
из следующих условий:

* У комментатора есть разрешение закрыть или снова открыть задачу 
в момент создания ссылки.
* Ссылка находится внутри сообщения коммита.
* Ссылка размещается как часть описания Pull Request'а.

В последнем случае задача будет закрыта или повторно открыта только в том случае, если
у Pull Request'а есть разрешения на это.

Кроме того, только Pull Request'ы и сообщения коммита могут создавать действие,
и только задачи можно закрывать или открывать повторно таким образом.

По умолчанию _ключевыми словами_ являются:

* **Closing**: close, closes, closed, fix, fixes, fixed, resolve, resolves, resolved
* **Reopening**: reopen, reopens, reopened

## Внешние трекеры

Gitea поддерживает использование внешних средств отслеживания
задач, а ссылки на задачи, размещённые на внешнем сервере, можно
создавать в Pull Request'ах. Однако, если внешний трекер использует
числа для выявления задач, они будут неотличимы от Pull Request'ов,
размещённых в Gitea. Чтобы решить эту задачу, Gitea позволяет использовать
маркер `!` Для идентификации Pull Request'ов. Например:

> Это задача [#1234](#), и она ссылается на внешний трекер.

> Это Pull Request [!1234](#), и он ссылается на Pull Request в Gitea.

Символы `!` и `#` могут использоваться взаимозаменяемо для задач и Pull Request'ов
_кроме_ того случая, когда требуется различие. Если репозиторий использует внешний трекер,
сообщение коммита для объединения по умолчанию будет использовать `!` В качестве ссылки.

## Сводка ссылок на задачи и Pull Request'ы

В этой таблице показаны различные виды перекрёстных ссылок для задач и Pull Request'ов.
В примерах, `User1/Repo1` относится к репозиторию, в котором используется ссылка, а
`UserZ/RepoZ` указывает на другой репозиторий.

| Ссылка в User1/Repo1      | Внешние задачи Repo1      | Внешние задачи RepoZ      | Должен воспроизводить            |
|---------------------------|:-------------------------:|:-------------------------:|----------------------------------|
| `#1234`                   |    нет                    |    Н/Д                    | Ссылку на задачу/pull 1234 в `User1/Repo1` |
| `!1234`                   |    нет                    |    Н/Д                    | Ссылку на задачу/pull 1234 в `User1/Repo1` |
| `#1234`                   |    да                     |    Н/Д                    | Ссылку на _внешнюю задачу_ 1234 для `User1/Repo1` |
| `!1234`                   |    да                     |    Н/Д                    | Ссылку на _PR_ 1234 для `User1/Repo1` |
| `User1/Repo1#1234`        |    нет                    |    Н/Д                    | Ссылку на задачу/pull 1234 в `User1/Repo1` |
| `User1/Repo1!1234`        |    нет                    |    Н/Д                    | Ссылку на задачу/pull 1234 в `User1/Repo1` |
| `User1/Repo1#1234`        |    да                     |    Н/Д                    | Ссылку на _внешнюю задачу_ 1234 для `User1/Repo1` |
| `User1/Repo1!1234`        |    да                     |    Н/Д                    | Ссылку на _PR_ 1234 для `User1/Repo1` |
| `UserZ/RepoZ#1234`        |    Н/Д                    |    нет                    | Ссылку на задачу/pull 1234 в `UserZ/RepoZ` |
| `UserZ/RepoZ!1234`        |    Н/Д                    |    нет                    | Ссылку на задачу/pull 1234 в `UserZ/RepoZ` |
| `UserZ/RepoZ#1234`        |    Н/Д                    |    да                     | Ссылку на _внешнюю задачу_ 1234 для `UserZ/RepoZ` |
| `UserZ/RepoZ!1234`        |    Н/Д                    |    да                     | Ссылку на _PR_ 1234 для `UserZ/RepoZ` |
| **Буквенно-цифровые идентификаторы задач:** | -       | -                         | - |
| `AAA-1234`                |    да                     |    Н/Д                    | Ссылку на _внешнюю задачу_ `AAA-1234` для `User1/Repo1` |
| `!1234`                   |    да                     |    Н/Д                    | Ссылку на _PR_ 1234 для `User1/Repo1` |
| `User1/Repo1!1234`        |    да                     |    Н/Д                    | Ссылку на _PR_ 1234 для `User1/Repo1` |
| _Не поддерживается_       |    Н/Д                    |    да                     | Ссылку на _внешнюю задачу_ `AAA-1234` для `UserZ/RepoZ` |
| `UserZ/RepoZ!1234`        |    Н/Д                    |    да                     | Ссылку на _PR_ 1234 в `UserZ/RepoZ` |

_Последний раздел предназначен для репозиториев с внешними системами отслеживания задач, которые используют буквенно-цифровой формат._

_**Н/Д**: не доступно._

Примечание: автоматические ссылки между репозиториями с различными типами задач (внешние или внутренние) не полностью поддерживаются
и могут отображать недействительные ссылки.
