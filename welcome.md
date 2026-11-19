---
title: Welcome to Poa
---
Poa is a small, quiet corner of the web that you own. It's a handful of Markdown files on a website: no accounts, no feeds ranked by someone else, no central server.

## How it works

Every Poa has one main file, `poa.md`. It says who you are, lists your posts, and lists the other Poas you read. That last list is the whole idea: it's how people find each other. Open someone's Poa and you see who *they* read, and you can hop from list to list, a bit like the old webrings.

Posts are plain `.md` files. You write them in Markdown, the same way you'd write a note.

If a Poa's host goes offline, its posts simply disappear until it's back. Nobody keeps copies.

## Where a Poa can live

A Poa is just files, so it can live almost anywhere. A reader on another site can only show your Poa if your host allows other websites to fetch your files.

**GitHub Pages.** If you made this Poa with the **Use this template** button, this is where you are. Turn on Pages in **Settings → Pages** (branch `main`, folder `/ (root)`), and your Poa is at `username.github.io/poa`. GitHub allows other sites to fetch your files automatically.

**Codeberg Pages.** Codeberg is a non-profit, community-run alternative to GitHub. Upload these files to a public repository called `poa`, put them on a branch called `pages`, and follow [Codeberg's Pages guide](https://docs.codeberg.org/codeberg-pages/) to publish it. Your Poa will be at `username.codeberg.page/poa`. Keep the `_headers` file that came with this template: it's what lets other Poas' readers fetch your files.

**Your own web host.** Upload the files to any folder on a host that serves HTTPS, for example `example.com/poa/`. Then add these lines to an `.htaccess` file in the same folder (on Apache hosts, which most shared hosts are):

```
Header set Access-Control-Allow-Origin "*"
AddType "text/plain; charset=utf-8" .md
```

The first line lets other Poas' readers fetch your files. The second makes browsers show `.md` files as text, with letters like ä and é intact.

## Make it yours

1. **Put your name in.** Edit `poa.md` and change `Your Name` to your name.
2. **Write your first post.** Create a file named with today's date, like `2026-11-20-first-post.md`, and start it like this:

   ```
   ---
   title: My first post
   date: 2026-11-20
   ---
   Write here. **Markdown** works.
   ```

   Then add a line for it at the top of the Posts list in `poa.md`:

   ```
   - [My first post](2026-11-20-first-post.md)
   ```

3. **Add Poas you read.** Under "Poas I read" in `poa.md`, add other Poas' addresses, one per line, like `marta.github.io/poa`. One is already there so you have somewhere to start.
4. **Remove this post.** Delete `welcome.md` and its line in `poa.md`.

Then give people your address, so they can add you to their lists.
