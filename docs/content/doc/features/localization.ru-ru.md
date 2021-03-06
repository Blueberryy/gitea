---
date: "2016-12-01T16:00:00+02:00"
title: "Локализация"
slug: "localization"
weight: 10
toc: true
draft: false
menu:
  sidebar:
    parent: "features"
    name: "Локализация"
    weight: 20
    identifier: "localization"
---

# Локализация

Локализация Gitea происходит через наш [Crowdin project](https://crowdin.com/project/gitea).

Для изменения **Английского** перевода можно сделать pull request, изменяющий соответствующий текст в 
[Английской локализации](https://github.com/go-gitea/gitea/blob/master/options/locale/locale_en-US.ini).

Для изменения **неанглийского** перевода см. Crowdin project выше.

## Поддерживаемые языки

Любой язык, указанный в вышеуказанном проекте Crowdin, будет поддерживаться, если переведено не менее 25%.

После того, как перевод был принят, он будет отражен в главном репозитории после следующей синхронизации Crowdin, которая обычно происходит после слияния любого PR.  
На момент написания это означает, что изменённый перевод может не появиться до следующего релиза Gitea.  
Если вы используете новейшую сборку, она должна появиться сразу после обновления после синхронизации изменения.
