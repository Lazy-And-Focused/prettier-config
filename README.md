# Конфигурация Prettier для Lazy And Focused

Общая [Prettier](https://prettier.io) конфигурация для проектов, поддерживаемых командой **Lazy And Focused**.

## Установка

Установите пакет как зависимость для разработки:

```bash
npm install @lazy-and-focused/prettier-config
```

> **Зависимость (peer dependency)**: требуется Prettier `^3.0.0`. Убедитесь, что он установлен в вашем проекте.

## Использование

### Через ESM-файл конфигурации (`.prettierrc.mjs`)

Создайте файл `.prettierrc.mjs` в корне вашего проекта:

```js
import config from '@lazy-and-focused/prettier-config';
export default config;
```

#### Расширение или переопределение конфигурации

Если вам нужно изменить некоторые правила, импортируйте базовую конфигурацию и объедините её с вашими настройками:

```js
// .prettierrc.mjs
import config from '@lazy-and-focused/prettier-config';

/**
 * @see  https:\\prettier.io\docs\configuration
 * @type { import("prettier").Config }
 */
export default {
  ...config,
  semi: false,               // пример переопределения
  printWidth: 100,           // пример переопределения
};
```

> **Примечание**: Этот пакет распространяется как ES-модуль (`"type": "module"`). Если ваш проект использует CommonJS, вы можете использовать подход с `package.json` или создать динамический импорт в файле `.prettierrc.cjs`:
>
> ```js
> // .prettierrc.cjs
> module.exports = async () => {
>   const config = await import('@lazy-and-focused/prettier-config');
>   return config.default;
> };
> ```
>
> или
>
> ```js
> // .prettierrc.cjs
> const config = require('@lazy-and-focused/prettier-config');
> 
> module.exports = {
>   config: config.default
> };
> ```

## Детали конфигурации

Эта конфигурация включает следующие настройки Prettier (и не только):

| Параметр                      | Значение         |
| ----------------------------- | ---------------- |
| `arrowParens`                 | `"always"`       |
| `bracketSpacing`              | `true`           |
| `bracketSameLine`             | `false`          |
| `trailingComma`               | `"all"`          |
| `singleQuote`                 | `true`           |
| `jsxSingleQuote`              | `true`           |
| `semi`                        | `true`           |
| `tabWidth`                    | `2`              |
| `useTabs`                     | `false`          |
| `printWidth`                  | `80`             |
| `endOfLine`                   | `"lf"`           |
| `proseWrap`                   | `"always"`       |

### Переопределения для Markdown

Для Markdown-файлов (`*.md`, `*.mdx`) `printWidth` уменьшен до `70` для лучшей читаемости.

Полную конфигурацию можно посмотреть в [`src/index.js`](./src/index.js).

## Авторы

- [Lazy And Focused](https://laf-team.ru)
  - [lanvalird](https://lanvalird.ru)
  - [FOCKUSTY](https://fockusty.vercel.app)

## Лицензия

[MIT](./LICENSE) © 2025 Lazy And Focused
