![goga logo](https://raw.githubusercontent.com/dapi/goga/master/assets/goga.png)

# goga

Языконезависимый менеджер однофайловых пакетов (версионированный `copy-paste`)

[![Build Status](https://travis-ci.org/dapi/goga.svg?branch=master)](https://travis-ci.org/dapi/goga)

## Зачем?

Бывают участки кода, которые, слегка модифицируясь копируются из проекта в проект. Ради них не рационально заводить и регистрировать отдельный пакет в типовых пакетных менеджерах, потому что:

1. Уходит время на создание и поддержку - необходимо создать тестовую инфраструктуру, описать спецификации, фактически придется создать ещё один проект
2. Придется отдельно вносить изменения в самом пакете, обновлять пакет в основном приложении и заново заниматься его интеграционным тестированием, а если пойдет что-то не так, обрытно переключаться в проект пакета, вносить там изменения в тесты и код, публиковать и тп.
3. Часто бывает, что проще слегка модифицировать код под новый проект, чем создавать универсальное решение подходящее всем проектам.

При этом хочется видеть историю изменений, централизованно хранить и делиться такими участками кода. Для таких случаев подходит `goga`.

`goga` это не замена `gem`, `bundle`, `npm`, `yarn` и тп, а дополнение. Он живет рядом и хорошо делает свою маленькую работу.

## Что на борту?

* Подключение однофайловых пакетов одной командой.
* Использует Ваш git и gists для хранения пакетов.
* Публикация пакета в общий репозиторий одной командой.
* Живет в системе контроля версий вашего приложения совместно с основным пакетным менеджером.
* Не зависит от языка программированя.
* Легко вность изменения в исходный код пакетов.
* Мультиплатформенное решение, написано на `golang`

## Установка

1. Установите `golang` в вашу ОС по [инструкции](https://golang.org/doc/install)

2. Установите `goga`

> go get github.com/dapi/goga

## Использование

Если кратко, то:

> goga

Гога расскажет какие у него есть команди и опции.

### Добавление модуля в проект

1. Возьмите ссылку на файл, который вы хотите добавить в проект. Это может быть прямая ссылка на github, например - `https://github.com/dapi/elements/blob/master/spinner.js`

2. Добавьте модуль в проект

> goga add https://github.com/dapi/elements/blob/master/spinner.js ./app/javascripts/

3. Используйте добавленный код `./spinner.js` привычным для вас способом.

Вы можете подключать и перемещать файл по проекту как вам удобно, используя проектную систему контроля версий.

### Публикация изменений

После того как вы внесли в модуль, находящийся в вашем проекте, изменения, оттестировали их и хотите ими поделиться или сохранить для будущего использования, опубликуйте его следующей командой.

> goga push ./app/javascripts/spinner.js

`goga` заглянет в исходник, найдет там ссылку на источник находящуюся в комментраии с префиксом `goga` и зальет туда изменения.

## Как устроены goga-модули

`goga`-модуль это обычный исходник на любом языке программирования, в который первой строкой автоматически добавлен `goga`-комментарий с адресом источника. Например:

```javascript
// goga https://github.com/dapi/elements/blob/master/spinner.js

customElements.define('dapi-spinner', class extends HTMLElement {} )
```

`goga`-комментарий добавляется автоматически при скачивании файла.

## Поддерживаемые источники модулей

* Любая прямая ссылка на файл, например: https://site.com/spinner.js
* Ссылка на исходник в github репозитории наблюдаемый в браузере типа https://github.com/dapi/elements/blob/master/spinner.js автоматически преобразуется в https://raw.githubusercontent.com/...

## Языковая поддержка

На данный момент поддерживюатся исходники следующих языков программирования
(определяется через расширение файла) - https://github.com/dapi/goga/blob/master/cmd/syntax.go#L31

Если Вам нужна поддержка других языкой - создайте issue или пришлите PR
