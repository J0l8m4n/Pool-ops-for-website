# Pool Ops website

The pool and beach Guest Book as an ordinary website, for the work tablet. It needs no Claude account.

Address, once GitHub Pages is on: https://j0l8m4n.github.io/Pool-ops-for-website/

On the tablet, open the address in Safari and use **Share > Add to Home Screen**, so it opens like an app.

## DEMO MODE

https://j0l8m4n.github.io/Pool-ops-for-website/demo/ is a demo of the same Guest Book with 300 made-up guests, for
showing the app to people. DEMO is at the top of every screen, and the **Demo guide** button walks through a shift.
It never touches real data: it saves only under its own "gb-demo:" names on the device, real lists can't be uploaded,
and demo and real backups refuse each other. Weather and lightning are live. **Reset demo** starts it over.
`demo/index.html` is built from Pool-and-beach-Ops (`docs/demo-mode.md` there).

## What it does

The same Guest Book staff use on claude.ai: Today, Check-in, Here now and the Guest Book, with the
Boucher Brothers "BB back drop" look.

| What | Where it comes from | How often |
|---|---|---|
| Pool weather | National Weather Service (`api.weather.gov`): rain chance, cloud cover, wind, gusts | Every 15 minutes |
| Today's setup | Worked out on the tablet from that forecast, with the same rules as the claude.ai version | Once a day, redone after 6:30 AM |
| Lightning alert | NOAA's GOES-19 lightning satellite (`noaa-goes19.s3.amazonaws.com`), within 8 miles of the pool | Every minute |
| Today's lists, check-ins, saved guests, lightning reports | Saved in the tablet's own browser | Right away |

## Where guest data lives

Only in the browser of the tablet it was entered on. It stays there after the website is closed or the tablet
restarts, and the page asks the browser to keep it for good.

- **Saved guest profiles**: every guest checked in to the main pool is saved, with any preferences added.
- **Archived**: once a day, when that day's lists are on the tablet, guests with no main pool check-in for a
  week, or past their check-out date, move here. Hotel guests with preferences stay in Saved. Nothing is
  deleted, and checking a guest in again moves them back.
- Always open the site the same way, from the home-screen icon. The icon and a Safari tab keep separate copies,
  so guests saved in one don't appear in the other. Private browsing keeps nothing.
- The address is part of where the data is kept: if the website moves to a new address, move the guests with
  **Copy backup** on the old address and **Restore backup** on the new one.

 None of it is in this repository, and it never
reaches the claude.ai Guest Book or other devices. Use **Copy backup** on the Guest Book tab now and
then, and paste the backup somewhere safe. Clearing Safari's website data erases it.

This repository is public: anyone with the address can open the page and read its code. That code holds
no guest names or lists.

## Updating the website

`index.html` is built from the Guest Book's source in the private repository J0l8m4n/Pool-and-beach-Ops.
Don't edit it by hand. To update, in Pool-and-beach-Ops:

```sh
npm test                 # every test must pass
npm run build:site       # writes site/index.html
```

Then copy `site/index.html` over `index.html` here and push. GitHub Pages republishes within a minute or two.

## Limits

- Lightning: the satellite places flashes to within a few miles and can miss small ones. Staff who see
  lightning or hear thunder still clear the pool and tap **Report lightning**.
- Data use: the lightning check downloads roughly 0.5 to 1 GB a day, so keep the tablet on Wi-Fi.
