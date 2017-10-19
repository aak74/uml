# Папка для описания основных алгоритмов

Для описания алгоритмов, use case и прочего используется язык разметки [plantuml](http://plantuml.com/)

В дальнейшем из этих файлов можно сгенерировать графические файлы с UML схемой.

Генерация картинки png из файла plantuml

    cat development.puml | plantuml -Tpng -pipe > development.png

Генерация картинки svg из файла plantuml

    cat development.puml | plantuml -Tsvg -pipe > development.svg

Для редактора [Atom](http://atom.io) есть [плагин](https://atom.io/packages/plantuml-viewer), в котором можно при редактировании сразу просматривать результат.

Есть [расширение](https://chrome.google.com/webstore/detail/plantuml-viewer/legbfeljfbjgfifnkmpoajgpgejojooj) для Chrome, которое позволяет просматривать схемы в браузере.
