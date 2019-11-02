# Сборка React приложений - Babel

Из курса [React + Redux - Профессиональная Разработка](https://www.udemy.com/course/pro-react-redux/)

## Установка Babel
```
npm install --save-dev @babel/core @babel/cli
```
Запуск babel:
```
npx babel src --out-dir build
```

Документация babel

https://babeljs.io/docs/en/


## Плагины Babel

Установка плагина
```
npm install --save-dev @babel/plugin-transform-template-literals
```

Запуск babel с плагином
```
npx babel src --out-dir build --plugins @babel/plugin-transform-template-literals
```

## Конфигурация Babel (.babelrc)

Конфигурационный файл babel: .babelrc (или babel.config.js)

Синтаксис babel - обычный JSON

```
{
    "plugins": [
        "@babel/plugin-transform-template-literals"
    ]
}
```

## Babel Presets

Preset - заранее сконфигурированный список плагинов
```
preset-env - отражает текущую стандартную версию языка JS
```
Устанавливается через npm 
```
npm install @babel/preset-env --save-dev
```
Конфигурационный файл babel:

```
{
    "presets": ["@babel/preset-env"] // or
    "presets": ["@babel/env"]
}
```

## Оптимизация сборки для конкретных браузеров

Конфигурационный файл .babelrc:

```
{
    "presets": [[ "@babel/env",
        {
            "targets": {
                "edge": "18",
                "chrome": "74"
        }}
    ]]
}
```

## Динамический выбор браузеров (browserslist)

[browserl.ist](https://browserl.ist/)

[Browserslist](https://github.com/browserslist/browserslist#browserslist-)

Конфигурационный файл .babelrc:
```
{
    "presets": [[ "@babel/env",
        {
            "debug": true,
            "targets": [
                "> 0.3%",
                "not ie > 0"
            ]
        }
    ]]
}
```

Вывод консоли:

```
@babel/preset-env: `DEBUG` option

Using targets:    
{
  "chrome": "49", 
  "edge": "17",   
  "firefox": "68",
  "ios": "11.3",  
  "safari": "5.1",
  "samsung": "4"  
}

Using modules transform: auto

Using plugins:
  transform-template-literals { "ios":"11.3", "safari":"5.1" }
  transform-literals { "safari":"5.1" }
  transform-regenerator { "chrome":"49", "safari":"5.1", "samsung":"4" }
  transform-exponentiation-operator { "chrome":"49", "safari":"5.1", "samsung":"4" }
  transform-async-to-generator { "chrome":"49", "safari":"5.1", "samsung":"4" }
  proposal-async-generator-functions { "chrome":"49", "edge":"17", "ios":"11.3", "safari":"5.1", "samsung":"4" }
  proposal-object-rest-spread { "chrome":"49", "edge":"17", "safari":"5.1", "samsung":"4" }
  proposal-unicode-property-regex { "chrome":"49", "edge":"17", "firefox":"68", "safari":"5.1", "samsung":"4" }
  proposal-json-strings { "chrome":"49", "edge":"17", "ios":"11.3", "safari":"5.1", "samsung":"4" }
  proposal-optional-catch-binding { "chrome":"49", "edge":"17", "safari":"5.1", "samsung":"4" }
  transform-named-capturing-groups-regex { "chrome":"49", "edge":"17", "firefox":"68", "safari":"5.1", "samsung":"4" }
  transform-modules-commonjs { "chrome":"49", "edge":"17", "firefox":"68", "ios":"11.3", "safari":"5.1", "samsung":"4" }
  proposal-dynamic-import { "chrome":"49", "edge":"17", "firefox":"68", "ios":"11.3", "safari":"5.1", "samsung":"4" }

Using polyfills: No polyfills were added, since the `useBuiltIns` option was not set.
Successfully compiled 1 file with Babel.
```

## Файлы конфигурации browserslist

Список браузеров можно хранить в следующих Файлах:

- .babelrc - в настройках preset-env
- package.json - в блоке browserslist
- в файле .browserslistrc - в каждой строке по отдельному выражению

## Polyfills

Polyfill - код, который добавляет глобальную функцию (если ее еще нет в браузере)

core-js - библиотека полифиллов

Конфигурация .babelrc:

```
"presets": [[ "@babel/env", {
            "corejs": "3",
            "useBuiltIns": "usage",
            ...
        }
]]
```

## Работа с JSX

@babel/preset-react - содержит трансформации, необходимые для работы с JSX кодом
```
npm install @babel/preset-react --save-dev 
```
Конфигурация .babelrc:
```
"presets": [
     [ "@babel/env", { ... }],
     "@babel/react"
]
```
