# Pool Ops website

The pool and beach Guest Book as an ordinary website, for the work tablet. It needs no Claude account.

Address, once GitHub Pages is on: https://j0l8m4n.github.io/Pool-ops-for-website/

On the tablet, open the address in Safari and use **Share > Add to Home Screen**, so it opens like an app.

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

Only in the browser of the tablet it was entered on. None of it is in this repository, and it never
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
