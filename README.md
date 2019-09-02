Рекомендации по написанию кода на C# (до версии 7.3 включительно)
================

Сайт https://www.csharpcodingguidelines.com

## От переводчика
Этот документ представляет из себя перевод [Coding Guidelines for C# (up to version 7.3)](https://github.com/dennisdoomen/CSharpGuidelines) от [Aviva Solutions](http://www.avivasolutions.nl).

## Как создать PDF файлы

1. В корне репозитория запустите `build.ps1` скрипт чтобы собрать HTML версию и чеклист.
2. В папке `Artifacts` откройте `CSharpCodingGuidelines.htm` в браузере и распечатайте как PDF. Используйте отступы по умолчанию и установите масштаб 80% для A4. 
3. Сделайте тоже самое для `CSharpCodingGuidelinesCheatsheet.htm`, но используйте альбомную ориентацию и минимальные отступы. Установите масштаб 84% чтобы вмесить чеклист в две колонки на А4. Убедитесь что нет отступов и разрашите печать фоновой графики чтобы вывести на печать цветные подсказки с дополнительной информацией. 

## Как собрать этот сайт

### Зависимости

* Ruby 2.4.x (2.5 и выше могут не работать из за того что библиотека `ffi` поддерживает только < 2.5)
* Ruby DevKit
* `bundler` гем (`gem install bundler`)

### Сборка

* Клонируйте репозиторий
* Перейдите в корень репозитория
* Запустите `bundle install`
* Запустите `bundle exec jekyll serve`

### Решение проблем

* Получаете ошибку связанную с `jekyll-remote-theme` и `libcurl`? Смотрите [эту ошибку на странице репозитория pages-gem](https://github.com/github/pages-gem/issues/526).
* Получаете ошибку `Liquid Exception: SSL_connect returned=1 errno=0 state=error: certificate verify failed`? Посмотрите [решение в репозитории Jekyll.](https://github.com/jekyll/jekyll/issues/3985#issuecomment-294266874)