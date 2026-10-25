# aminabaktiyarova.com

Personal site. Jekyll on GitHub Pages.

## Publishing a blog post

1. Copy `POST-TEMPLATE.md` into `_posts/`.
2. Rename it `YYYY-MM-DD-short-title.md`.
3. Fill in the title, date, tags, description, and the text.
4. Commit and push. The post appears in a minute or two.

Tags are free: type whatever you want. The filter bar on `/blog/` builds itself
from the tags used across all posts.

## Editing a page

Each page is one file in the root: `index.html` (About), `research.html`,
`abc.html`, `abe.html`, `contact.html`, `blog.html`. Edit the text between the
tags and push.

## Changing prices, Shop items and links

Everything on the Shop page (names, descriptions, prices in EUR and KZT, and
Tribute links) lives in `_data/shop.yml`. When an item has no Tribute link, its
button opens a Telegram chat instead.

Telegram, YouTube and email live in `_config.yml`. Change them there and every
page updates.

## Photos

`assets/photos/`. The row on the About page shows them in filename order.
