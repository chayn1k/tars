Работа с JS
===========

На данный момент сборщик работает только с обычным js. Если требуется использовать coffeescript или TypeScript или что-то еще, то можно поправить таск js-processing или написать мне, если ничего не получается. В дальнейшем планируется сделать это опционально.

По умолчанию js находится в 2-ух местах:
*   В папке со статикой, в подпапке с именем js
*   В каждом отдельном модуле.

Можно добавить свои папки для js, используя соответствующую <a href="https://github.com/artem-malko/tars/blob/master/docs/options.md#jspathstoconcatbeforemodulesjs-%D0%B8-jspathstoconcataftermodulesjs">опцию</a> в конфиге сборщика.

Весь js-код собирается в один отдельный файл, кроме js-файлов, которые находятся в директории separate-js. Эти файлы просто переносятся как есть в готовую сборку. Примером такого файла является html5shiv.js

Файлы собираются в следующем порядке:
*   static/js/libraries (включая подпапки)
*   static/js/plugins (включая подпапки)
*   все файлы, пути к которым находятся в опции jsPathsToConcatBeforeModulesJs
*   js-файлы модулей
*   все файлы, пути к которым находятся в опции jsPathsToConcatAfterModulesJs

Перед сборкой в один файл весь js-код (кроме файлов из static/js) проверяется на соответствие code-style (который описан в конфигурационном файле .jscsrc в коре проекта), а также производится поиск ошибок. Данный проверки <a href="https://github.com/artem-malko/tars/blob/master/docs/options.md#usejslintandhint">опциональны</a>.<br/>Проверкой файлов из jsPathsToConcatBeforeModulesJs и jsPathsToConcatAfterModulesJs можно управлять отдельно, опциями lintJsCodeBeforeModules и lintJsCodeAfterModules.<br/>
Если требуется отключить проверку отдельного файла, то нужно добавить в начало его имени '_'.

