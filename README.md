# Library Books Rehoming

A static catalog of Judaica reference books leaving the library, with a passphrase gate and a reservation sign-up backed by a Google Sheet.

## How it works

- `index.html` holds the catalog (book data embedded) and all page logic.
- `config.js` holds the settings you may need to change: the Apps Script web app URL, the passphrase, the contact email, and the Google Sheet link.
- `covers/`, `spines/`, `shelves/` are the images.
- Reservations are written to the Google Sheet through a small Google Apps Script web app (`Code.gs`, kept in the project folder, not in this repo).

## Turning on reservations

1. Open the Google Sheet "Library Books Rehoming – Reservations".
2. Extensions → Apps Script. Replace the contents of `Code.gs` with the `Code.gs` from the project folder. Save.
3. Deploy → New deployment → Web app. Execute as **Me**; who has access **Anyone**. Deploy and authorize.
4. Copy the web app URL (ends in `/exec`) into `API_URL` in `config.js`. Commit and push. GitHub Pages updates in about a minute.

## Changing the passphrase

Change `PASSPHRASE` in both `config.js` and `Code.gs` (then redeploy the web app as a new version). The passphrase is visible in the page source; it keeps casual visitors out, not determined ones.

## Admin view

Click "Admin sign-in" at the bottom of the page and enter `ADMIN_KEY` from `Code.gs`. The admin tab shows every reservation with emails, sortable and grouped by person, with release buttons and a CSV download. The Google Sheet itself always has the full list too.
