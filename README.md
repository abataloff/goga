# goga

Менеджер однофайловых модулей. Использует Ваш git и gists для хранения пакетов.

## Зачем?

* У вас есть участки кода которые вы копируете из проекта в проект, слегка модифицируя по ходу
* Вы не считаете нужным оформлять их в типичные пакеты, так как это занимает время и усложняет изменение модуля под конретное приложение.
* Вы хотите контроллировать историю изменения модуля.
* Вы хотите делиться кодом с другими.

В таких случаях проще использовать `goga`. Он одной командой добавляет модуль в ваш проект, контроллирует и публикует его изменения. Таким модулем легко делиться и поддерживать.

## Преимущества

* Версионированная альтернатива `copy-paste`
* Небольшие готовые решения можно подключать в проект целиком
* Легко вность изменения
* Легко публиковать
* Мультиплатформенное решение. Написано на `golang`

## Использование

### Добавление модуля в проект

1. Возьмите ссылку на файл, который вы хотите добавить в проект. Это может быть прямая ссылка на github, например - `https://github.com/dapi/elements/blob/master/spinner.js`

2. Добавьте модуль в проект

> goga add https://github.com/dapi/elements/blob/master/spinner.js ./app/javascripts/

3. Используйте добавленный код привычным для вас способом.

Вы можете подключать и перемещать файл по проекту как вам удобно, используя проектную систему контроля версий.

### Публикация изменений

После того как вы внесли в модуль, находящийся в вашем проекте, изменения, оттестировали их и хотите ими поделиться или сохранить для будущего использования, опубликуйте его следующей командой.

> goga push ./app/javascripts/spinner.js

`goga` найдет адрес репозитория, в котором хранится модуль в первых строках комментария и зальет туда изменения под вашими текущими доступами.

## Как устроены goga-модули

`goga`-модуль это обычный исходник на любом языке программирования, в который, при установке, первой строкой добавляется адрес источника вида: `// goga https://...`
