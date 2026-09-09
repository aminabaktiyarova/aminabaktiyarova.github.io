# Putting the site live

Follow this top to bottom. Every command is one line: copy it, paste it into
Terminal, press Enter.

Your favicon lives at `assets/img/favicon.svg` in the repo. Step 9 saves it and
step 12 puts it back, so you do not need to do anything about it by hand.

---

## Part 1: get the new files onto your Mac

1. Download `site.zip` from the chat.

2. Go to your Downloads folder and double-click `site.zip`. It becomes a folder
   called `site`.

3. Leave it there. The commands below assume it is at `~/Downloads/site`.

---

## Part 2: open the repo in Terminal

4. Open Terminal: press Cmd and Space together, type `Terminal`, press Enter.

5. Go to your copy of the repo:

```
cd ~/aminabaktiyarova.github.io
```

If that says "no such file or directory", find it with this:

```
find ~ -maxdepth 4 -type d -name "aminabaktiyarova.github.io" 2>/dev/null
```

Then type `cd ` and paste the path it printed.

If it printed nothing, the repo is not on this Mac yet. Get it with:

```
cd ~ && git clone https://github.com/aminabaktiyarova/aminabaktiyarova.github.io.git && cd aminabaktiyarova.github.io
```

6. Confirm you are in the right folder. This should list `_config.yml`, `CNAME`,
   `abc`, `abe`, `assets` among other things:

```
ls
```

---

## Part 3: back up, then replace

7. Make sure your local copy matches GitHub:

```
git pull
```

8. Copy the whole repo to your Desktop, in case you want to undo this:

```
cp -r . ~/Desktop/site-backup
```

9. Save the favicon out of the repo for a moment:

```
cp assets/img/favicon.svg ~/Desktop/favicon.svg
```

10. Delete the old site files. This keeps `.git` (your history) and `CNAME`
    (your domain), and removes everything else:

```
find . -maxdepth 1 ! -name . ! -name .git ! -name CNAME -exec rm -rf {} +
```

11. Copy the new files in:

```
cp -r ~/Downloads/site/. .
```

12. Put the favicon back:

```
mkdir -p assets/img && cp ~/Desktop/favicon.svg assets/img/favicon.svg
```

---

## Part 4: check before you push

13. Your domain file must still be there. This should print
    `aminabaktiyarova.com`:

```
cat CNAME
```

If it prints nothing, stop here. Copy everything back from
`~/Desktop/site-backup` and tell me what happened.

14. The favicon must be there. This should print `favicon.svg`:

```
ls assets/img/
```

15. See what is about to change:

```
git status
```

You will see a long list of deleted old files and added new ones. That is
correct.

---

## Part 5: push

16. Stage everything:

```
git add -A
```

17. Commit:

```
git commit -m "Rebuild site as a personal hub"
```

18. Push:

```
git push
```

GitHub takes one to two minutes to rebuild. If the build fails you get an email,
and the Actions tab on the repository page shows what broke.

---

## Part 6: check it worked

Open each of these in a browser:

- `aminabaktiyarova.com` shows the new About page with the photo row
- `aminabaktiyarova.com/research/` shows the three projects
- `aminabaktiyarova.com/abc/services/` bounces you to `/abc/`
- `aminabaktiyarova.com/abc/blog/` bounces you to `/blog/`
- `aminabaktiyarova.com/nonsense` shows the new "Page not found" page
- The door icon appears in the browser tab

---

## If you want to see it before pushing

Between step 12 and step 16, run:

```
bundle install && bundle exec jekyll serve
```

Open the address it prints, usually `http://127.0.0.1:4000`. Press Ctrl and C
together in Terminal to stop it. This needs Ruby installed. If it errors out,
skip it, push, and check the live site instead.

---

## Undoing it

If you have not pushed yet:

```
git checkout . && git clean -fd
```

If you have already pushed, tell me and I will give you the command to roll back
that commit.

---

## What changed in _config.yml

- `url` now points at `https://aminabaktiyarova.com`. It was pointing at the
  github.io address, which was putting the wrong domain into your canonical tags
  and your sitemap.
- The blog permalink moved from `/abc/blog/:year/:slug/` to `/blog/:year/:slug/`.
- `boosty` removed.
- `jekyll-redirect-from` added. This is what makes the old AB:C URLs forward
  instead of breaking.
- New posts default to the Blog section of the navigation instead of AB:C.
