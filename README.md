# Durfee STEAM Lab website

The lab's site, built with [Hugo](https://gohugo.io). Pages are Markdown files. Hugo turns them into HTML.
Pushing to the `main` branch on GitHub makes Cloudflare rebuild and publish the site.

## Reading the code

Every template, the stylesheet, the config files and the main content pages have comments explaining what they do and how Hugo's template language works. A good order to read them in: `hugo.toml`, `layouts/_default/baseof.html`, `layouts/index.html`, `layouts/partials/header.html`, then `static/css/style.css`.

## Where things are

| Folder or file | What it holds |
| --- | --- |
| `content/` | **The pages.** Each `.md` file is one page. The folder path is the web address. |
| `content/posts/` | Bulletin board posts. |
| `layouts/` | HTML templates that wrap the content. Start with `_default/baseof.html`. |
| `static/` | Files copied as they are: `css/style.css`, `favicon.svg`, and any images. |
| `hugo.toml` | Site settings and the top menu. |
| `wrangler.jsonc` | Tells Cloudflare which folder to publish. |
| `archetypes/` | Starting templates for `hugo new`. |

## Add a bulletin board post

1. Create a file in `content/posts/`, for example `science-fair-signup.md`.
2. Start it with this, then write the post below:
   ```
   ---
   title: "Science fair sign-up"
   date: 2026-10-20
   ---
   ```
3. Commit and push. The newest five posts show on the home page.

(`hugo new posts/science-fair-signup.md` makes the file for you.)

## Add or change a page

Edit the `.md` file. Files named `_index.md` are section pages, such as Resources. Other files are single pages.
Put a `weight:` in the front matter to control the order in lists. Add `toc: true` to show a contents list.

## Page conventions used here

- `{{% admonition type="note" title="Title" %}} ... {{% /admonition %}}` makes a note box. Types are `note`, `todo` and `draft`.
- `{{% checkpoint %}} ... {{% /checkpoint %}}` makes a green "you should see this now" box.
- `<span class="todo">[text]</span>` marks something still to fill in. It shows highlighted in yellow.
- `## A Heading {#my-id}` gives a heading a fixed address, so other pages can link to `/page/#my-id`.
- The cards on index pages are plain HTML (`<div class="cards">`) inside the Markdown.

## Preview on your own computer

1. Install Hugo (extended version).
2. Run `hugo server` in this folder and open the address it prints.
3. Edits show up as you save.

## Deploying

Cloudflare runs `hugo`, which builds the site into `public/`, then publishes that folder.
`public/` is not saved in Git, because the build makes it fresh each time.
