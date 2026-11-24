# Poa

A Poa is a small personal site made of Markdown files. Every Poa lists the other Poas its owner reads, and you find your way around by hopping from list to list. There is no central server, no signup and no algorithm.

## Make your own Poa

1. Go to [github.com/gearnoodle/poa-template](https://github.com/gearnoodle/poa-template) and press the green **Use this template** button, then **Create a new repository**. Name it `poa` and make it **Public**.
2. In the repository, go to **Settings → Pages**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.
3. Edit `poa.md`: put your name in it, and a category on the `category:` line (see below).
4. On the repository page, click the ⚙ next to **About** and add the topic `poa`, so readers can find you.
   Not on GitHub, or want to be sure? Add your address to the Poa directory: [step-by-step instructions](https://github.com/gearnoodle/poa-directory#add-your-poa). Anyone can browse the directory at [gearnoodle.github.io/poa-directory](https://gearnoodle.github.io/poa-directory/).
5. After a minute your Poa is live at `https://<your-username>.github.io/poa/`.

Your Poa's address is `<your-username>.github.io/poa`. Give it to people so they can add you to their lists.

## Writing a post

1. Add a new file, for example `2026-11-20-my-post.md`. Starting the name with the date keeps posts in order.
2. Start it with a short header, then write in Markdown:

   ```markdown
   ---
   title: My post
   date: 2026-11-20
   ---
   Write here. **Markdown** works.
   ```

3. Add a line for it at the top of the Posts list in `poa.md`.

## Reading others

Add their addresses under "Poas I read" in `poa.md`, one per line:

```markdown
## Poas I read
- marta.github.io/poa
- jordi.github.io/poa
```

---

## The format (version 1)

**Address.** A Poa's address is the folder that holds `poa.md`. Readers add `/poa.md` themselves and assume `https://`. A full URL ending in `.md` is also accepted.

**`poa.md`** is the only required file:

```markdown
---
version: 1
name: Manu Järvinen
category: tech
---
## Posts
- [Hello, Poa](2026-11-19-hello.md)

## Poas I read
- marta.github.io/poa
```

- The header sits between two `---` lines and holds `key: value` lines. `version: 1` is required. `name` is the name shown to readers.
- `category` (optional) is one word for what the Poa is mostly about. Capitals don't matter. Any word works; some suggestions: food, travel, tech, books, art, music, life. A Poa without one counts as "uncategorized".
- `search: no` (optional) asks readers and crawlers to leave this Poa out of search results, "read by" lists and indexes. Its "Poas I read" list can still be followed for hopping.
- `## Posts` lists posts as Markdown links, newest first. Links are relative to `poa.md`.
- `## Poas I read` lists other Poas' addresses, one per line.

**Posts** are `.md` files with a header (`title`, `date` as `YYYY-MM-DD`) followed by Markdown (CommonMark). A post can have its own `category` when it differs from its Poa's: a post's category is its own `category` if set, otherwise its Poa's. Readers must not run raw HTML in posts and only load images from the post's own site.

**Hosting.** Any host works if it serves the files over HTTPS. For web-based readers, the host must also allow cross-site requests (the header `Access-Control-Allow-Origin: *`). GitHub Pages does this by default. On Codeberg Pages, a `_headers` file adds it; on your own Apache host, `.htaccess` does (see `welcome.md` in the template).

**Being found.** The template's `index.html` carries `<meta name="poa" content="1">`, `<link rel="alternate" type="text/markdown" title="Poa" href="poa.md">` and a visible "This is a Poa" line, so crawlers and search engines can recognise a Poa from its homepage on any host. To stay out of search, remove them and add `search: no`.

**Offline means gone.** When a Poa's host is unreachable, readers show it as unreachable. They don't keep or pass on copies.

## This reader

`index.html` is a reader that shows your own Poa and lets you hop to the Poas you read. It's a single file with no build step.

**Search** follows the "Poas I read" lists outward from your Poa, up to 3 steps away by default (the Poas you read, the Poas they read, and so on), and searches names, post titles and the text of each Poa's 10 newest posts. With **Everywhere** chosen under the search box, it also searches the Poas listed in the [Poa directory](https://github.com/gearnoodle/poa-directory), an opt-in list anyone can add their own Poa to by pull request, whatever host it's on. It also asks GitHub for public repositories with the topic `poa` or named `poa` that have Pages turned on, and searches the ones that turn out to be Poas. GitHub answers only a few such questions a minute without a login, so the reader asks once and keeps the answer for 30 minutes. The directory's address is `DIRECTORY` at the top of the script: point it at another list in the same format, or set it to `""` to leave it out. Results can be narrowed by category with the buttons above them, and a post's category links to everything in that category.

**Read by** lists the Poas whose "Poas I read" list includes yours. It's worked out from the public lists, using the same walk, the Poa directory and GitHub search, so a new reader shows up the next time the page runs and finds them.

Everything runs in your browser; nothing is collected anywhere. The limits are at the top of the script in `index.html`. `markdown-it.min.js` is the Markdown renderer it uses (MIT licence). `.nojekyll` tells GitHub Pages to serve the `.md` files as they are.
