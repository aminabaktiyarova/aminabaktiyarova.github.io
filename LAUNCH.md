# Launch guide

Follow these in order. Anything in ALL CAPS is something you replace with your
own value.

One thing worth knowing before you start: the site is public the moment GitHub
Pages is switched on. Nobody will know the address, but write the text before
you point your domain at it.

---

## 1. Put the files somewhere permanent

Do not work inside Downloads. Files get cleared out of there by accident.

1. Double click `aminabaktiyarova-site.zip`. It unpacks to a folder called
   `site`.
2. Rename that folder to `aminabaktiyarova.com` and drag it to your home folder,
   the one with your name on it in the Finder sidebar.

From here on, the folder lives at `~/aminabaktiyarova.com`.

---

## 2. Get a text editor

Do not use TextEdit. It saves rich text and will silently break the files.

Install Visual Studio Code, free, from `code.visualstudio.com`. Open it, then
File, Open Folder, and choose `aminabaktiyarova.com`. You will see the whole
site in the sidebar and can click between files.

---

## 3. Fill in the settings file

Open `_config.yml`.

Eight values say `REPLACE_ME`. Replace each with your real link:

- `telegram_channel`, your public channel
- `telegram_direct`, your personal username for direct messages
- `telegram_questions_bot`, the anonymous questions bot
- `youtube`
- `email`
- `boosty`
- `booking_url`, where a consultation booking starts

The four Tribute product links are already correct.

There is deliberately no `CNAME` file in the folder. That file is what tells
GitHub to serve the site at your own domain, and if it arrives before your DNS
is ready the site will not load at any address. GitHub creates it for you in
step 10, at the right moment.

---

## 4. Write the text

Everything in square brackets is a slot for you. Delete the brackets along with
the placeholder text inside them.

In VS Code, press Cmd+Shift+F and search for `[` to see every slot, grouped by
file. Work down the list.

The lines at the top of each file between the two `---` lines are the page
title, the single line that sits under the title, and the description that shows
in Google results. Everything below is the page body.

Pages, in the order I would write them:

| Page | File |
|---|---|
| AB:C main page | `abc/index.md` |
| Services | `abc/services.md` |
| How we work | `abc/process.md` |
| Digital products | `abc/products.md` |
| Contact | `abc/contact.md` |
| Home | `index.html` |
| AB:E | `abe/index.md` |
| Blog index | `abc/blog.md` |
| Blog tag pages | `abc/tags/` |
| Not found page | `404.html` |
| Footer | `_layouts/default.html` |

---

## 5. Install git

Open Terminal. It is in Applications, Utilities, or press Cmd+Space and type
Terminal.

Type this and press return:

```
git --version
```

If it prints a version number, you already have it. If a box appears offering to
install developer tools, click Install and wait. It takes a few minutes.

Then set yourself up. Use the email address on your GitHub account:

```
git config --global user.name "Amina Baktiyarova"
git config --global user.email "YOUR_GITHUB_EMAIL"
git config --global credential.helper osxkeychain
git config --global init.defaultBranch main
```

---

## 6. Make a token so git can log in

GitHub stopped accepting account passwords from the command line. You need a
token instead. You do this once.

1. On GitHub, click your avatar, top right, then Settings.
2. Bottom of the left sidebar, Developer settings.
3. Personal access tokens, then Tokens (classic).
4. Generate new token, then Generate new token (classic).
5. Note: `site`. Expiration: 90 days or No expiration, your call.
6. Tick the box marked **repo**. Nothing else.
7. Generate token, then copy it. You cannot see it again after you leave the
   page, so paste it somewhere safe for the next five minutes.

---

## 7. Replace the repository

1. Go to your `aminabaktiyarova.github.io` repository.
2. Settings, scroll to the bottom, Danger Zone, Delete this repository. Type the
   name to confirm.
3. Back on GitHub, click the plus icon top right, New repository.
4. Repository name: `aminabaktiyarova.github.io`, spelled exactly, using your
   real GitHub username in place of `aminabaktiyarova` if it differs.
5. Set it to **Public**. GitHub Pages will not publish a private repository on a
   free account.
6. Do not tick Add a README, .gitignore, or a licence. Leave it empty.
7. Create repository.

---

## 8. Upload the site

In Terminal, one line at a time. Replace USERNAME with your GitHub username:

```
cd ~/aminabaktiyarova.com
git init
git add -A
git commit -m "New site"
git remote add origin https://github.com/aminabaktiyarova/aminabaktiyarova.github.io.git
git branch -M main
git push -u origin main
```

On the last command it asks for a username and a password. Username is your
GitHub username. For the password, paste the token from step 6. It will not show
anything as you paste, that is normal. Press return.

macOS saves it, so you will not be asked again.

Refresh the repository page on GitHub and your files should be there.

---

## 9. Switch on GitHub Pages

1. In the repository, Settings, then Pages in the left sidebar.
2. Source: Deploy from a branch.
3. Branch: `main`, folder: `/ (root)`. Save.
4. Wait two or three minutes. The Actions tab shows a job called
   `pages build and deployment`. A green tick means it worked.
5. Open `https://aminabaktiyarova.github.io`.

Read every page. Anything wrong, fix it in VS Code, then:

```
cd ~/aminabaktiyarova.com
git add -A
git commit -m "Fixes"
git push
```

Changes appear about a minute later. Repeat as often as you like.

---

## 10. The domain

Only do this once the github.io version looks right.

**Buy it.** `aminabaktiyarova.com` from any registrar, roughly 10 to 15 USD a
year. Namecheap, Porkbun, Cloudflare and GoDaddy all work.

**Point it at GitHub.** In your registrar's DNS panel, delete any records the
registrar created for `@` by default, then add these five:

| Type | Name | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | USERNAME.github.io |

The `www` record matters even though you are using the bare domain. It is the
one that keeps working if GitHub ever changes those four addresses.

**Tell GitHub.** Repository Settings, Pages, Custom domain. Type
`aminabaktiyarova.com` and Save.

DNS can take anywhere from ten minutes to a full day. GitHub will show a DNS
check that goes green when it is ready.

**Important:** saving the custom domain makes GitHub add a `CNAME` file to your
repository. Your copy on the Mac does not have it, so before your next push you
must run:

```
cd ~/aminabaktiyarova.com
git pull
```

Skip this and your next push will be rejected.

**Turn on HTTPS.** Back in Settings, Pages, tick Enforce HTTPS. If it is greyed
out, the certificate is still being issued. Wait an hour and check again. If it
is still greyed out after a day, remove the custom domain, save, add it again,
save.

---

## 11. Before you tell anyone

- Open every page on your phone as well as your laptop.
- No square brackets left anywhere. In VS Code, Cmd+Shift+F, search `[`.
- No `REPLACE_ME` left. Same search.
- Every link in the footer and on the contact page opens the right place.
- All four Tribute links open the right product.
- The old Notion blog is archived and no longer linked from your channels.
- Ko-fi is gone from every bio and pinned message, not only from the site.

---

## Publishing a blog post, from now on

1. In VS Code, open `_drafts/TEMPLATE.md` and Save As into the `_posts` folder.
2. Name it `YYYY-MM-DD-short-title.md`, for example
   `2026-09-04-uk-scholarship-deadlines.md`.
3. Fill in the title, the one line summary, and exactly one tag:
   `ielts-english`, `strategy`, or `research`.
4. Write the post in plain markdown underneath.
5. In Terminal:

```
cd ~/aminabaktiyarova.com
git add -A
git commit -m "New post"
git push
```

It appears on the blog page and on its tag page by itself. You never edit a
list by hand.

---

## Editing anything else

Same three commands every time. Edit in VS Code, then:

```
cd ~/aminabaktiyarova.com
git add -A
git commit -m "WHAT YOU CHANGED"
git push
```

---

## Where things live

```
_config.yml          every link, handle, and setting
_data/abc_nav.yml    the AB:C menu
_layouts/            page shells
_includes/           the door, the book, and the AB mark, as SVG
_posts/              published blog posts
_drafts/TEMPLATE.md  the post template
assets/css/style.css the whole design, one file
assets/img/          favicon
```

Colours, typefaces and spacing are variables at the top of
`assets/css/style.css`. Change one there and it changes everywhere.

---

## If something breaks

**Push rejected.** Run `git pull`, then push again.

**Site not updating.** Check the Actions tab for a red cross. Click into it to
see which file it is complaining about.

**Page is blank or looks wrong.** Usually a missing `---` line at the top of a
file, or a smart quote. Make sure VS Code is saving plain text.

**Everything looks unstyled.** The stylesheet path is wrong, which happens if
`baseurl` in `_config.yml` was changed. It should be empty quotes.
