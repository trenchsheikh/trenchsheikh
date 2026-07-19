# Setup — auto-updating profile README

Design + stats engine adapted from [Andrew6rant/Andrew6rant](https://github.com/Andrew6rant/Andrew6rant) (credit to Andrew Grant).

## 1. Create the repo
Create a **public** repo named exactly `trenchsheikh` (same as your username). GitHub treats its README as your profile page.

## 2. Add these files
```
README.md
dark_mode.svg
light_mode.svg
today.py
cache/requirements.txt
.github/workflows/build.yaml
```
Also create an empty `cache/` folder (the requirements.txt inside keeps it).

## 3. Set your birthday
In `today.py`, find the line with `datetime.datetime(2000, 1, 1)` and change it to your real birthday — this powers the "Uptime" line.

## 4. Create a token
GitHub → Settings → Developer settings → Personal access tokens (classic) → generate with scopes: `repo`, `read:user`.

## 5. Add the secret
In the `trenchsheikh` repo → Settings → Secrets and variables → Actions → New repository secret:
- Name: `ACCESS_TOKEN`, value: your token

## 6. Run it
Push to main (or go to Actions → "README build" → Run workflow). The script queries the GitHub GraphQL API, counts your commits, repos, stars, followers and every line of code you've ever added/deleted, then rewrites the numbers inside both SVGs. It re-runs daily at 4am UTC.

First run takes a few minutes (it walks every repo to count LOC); after that it's cached.

## Tweaking the card
Both SVGs are plain text — open them and edit any line (OS, Host, Hobbies, links, etc.). Keep the `id="..."` attributes intact; those are the fields the script overwrites.
