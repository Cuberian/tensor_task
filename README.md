# tensor_test

## Project setup
```
npm install
```

С
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

## Пояснения к входным параметрам
### Spoiler
* title - текст который будет находиться в шапке спойлера;
* content - текст для контента спойлера;
* togglerSize - задает размер тогглера. Может быть трех вариантов: small, medium, big;
* togglerStyle - задает стиль тогглера. В виде строки передаются названия классов;
* titleStyle - задает стиль блока с заголовком спойлера. В виде строки передаются названия классов;
* contentStyle - задает стиль блока с контентом спойлера. В виде строки передаются названия классов;
* togglerState - состояние спойлера. Может быть двух вариантов: open, close. В зависимости от варианта спойлер на старте будет открыт или закрыт;
* orderNumber - порядковый номер спойлера. Данный входной параметр нужен только для аккардиона. Определяет порядковый номер спойлера в аккардионе для итеракций с ним через события.
### Accordion
* accordionItems - массив элементов для аккардиона. Внутри этого массива лежат объекты со свойствами title и content, которые являются текстовым содержимым заголовка спойлера и его контента соответственно;
* openMode - поведение аккардиона при открытии спойлеров. Может быть двух вариантов: one, many. В зависимости от выбранного значения одновременнно может быть открыт один или несколько спойлеров соответсвенно
* openElements - массив чисел, числа в котором равняются порядковым номерам спойлеров в аккардеоне. При отображении аккардеона будут открыты все аккардеоны, порядковые номера которых присутсвуют в массиве. Если выбрано значение "one" в openElements, то будет открыт только первый элемент в массиве
* togglerSize - адает размер тогглеров в аккардеоне. Может быть трех вариантов: small, medium, big;
* togglerStyle - задает стиль тогглеров в аккардеоне. В виде строки передаются названия классов;
* titleStyle - задает стиль блоко с заголовками спойлеров в аккардеоне. В виде строки передаются названия классов;
* contentStyle - задает стиль блока с контентами спойлеров в аккардеоне. В виде строки передаются названия классов;
