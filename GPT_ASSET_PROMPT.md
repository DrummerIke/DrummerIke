# Prompt for GPT: add G7 start page files

Use this prompt when asking GPT or another assistant to prepare the missing upload package for hosting.

```text
Нужно подготовить статическую стартовую страницу G7 для загрузки на хостинг.

Важно: все файлы должны лежать в одной папке рядом, без вложенных директорий и без переименования, потому что HTML и manifest используют относительные пути `./...`.

В папке должны быть такие файлы:

1. `index.html`
2. `manifest.webmanifest`
3. `favicon.svg`
4. `icon-180.png`
5. `icon-192.png`
6. `icon-512.png`
7. `README.md`

Текстовые файлы `index.html`, `manifest.webmanifest`, `favicon.svg` и `README.md` уже есть в репозитории. Нужно вставить/создать рядом с ними только недостающие PNG-иконки:

- `icon-180.png` — PNG 180x180 для iOS Apple Touch Icon.
- `icon-192.png` — PNG 192x192 для favicon/PWA Android и для отображения на странице.
- `icon-512.png` — PNG 512x512 для PWA manifest.

Требования к PNG:

- Формат: PNG.
- Фон: тёмный или градиентный в стиле G7.
- Надпись/логотип: `G7` по центру.
- Имена файлов должны быть строго такими: `icon-180.png`, `icon-192.png`, `icon-512.png`.
- Не складывать картинки в отдельную папку.
- Не менять пути в `index.html` и `manifest.webmanifest`, если файлы кладутся рядом.

После вставки PNG итоговая структура папки на хостинге должна быть такой:

```text
g7/
├── index.html
├── manifest.webmanifest
├── favicon.svg
├── icon-180.png
├── icon-192.png
├── icon-512.png
└── README.md
```

Проверь, что в `index.html` остаются такие ссылки:

```html
<link rel="icon" href="./favicon.svg" type="image/svg+xml" />
<link rel="icon" href="./icon-192.png" sizes="192x192" type="image/png" />
<link rel="apple-touch-icon" href="./icon-180.png" sizes="180x180" />
<link rel="manifest" href="./manifest.webmanifest" />
```

Проверь, что в `manifest.webmanifest` остаются PNG-иконки:

```json
"icons": [
  {
    "src": "./icon-192.png",
    "sizes": "192x192",
    "type": "image/png"
  },
  {
    "src": "./icon-512.png",
    "sizes": "512x512",
    "type": "image/png"
  }
]
```

После загрузки на хостинг обычное открытие страницы должно показывать экран G7, а запуск с домашнего экрана в standalone-режиме должен перенаправлять на:

```text
https://sites.google.com/view/borkg7/
```
```
