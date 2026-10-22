# Shani & Neha — Wedding Invitation

Static website (no build step). Everything is in `index.html`; media lives in `assets/`.

**Full change guide:** see `GUIDE.md` · **Master prompt to recreate everything:** see `PROMPT.md`

## Files YOU must upload into `assets/` (exact names, case-sensitive)

| File | Used for |
|---|---|
| `first seal.webp` | Opening cover |
| `Intro Final.mp4` | Intro video (plays fully, can't be skipped) |
| `bg-music.mp3` | Background music (loops) |
| `om ganehya namah.webp` | Ganesh artwork in the invitation card |
| `neha shani.webp` | Closing couple photo |
| `guest.webp` | Wax seal button that opens the family gallery |
| `Aryan.webp`, `Musu.webp`, `Sanjana.webp`, `Papa.webp`, `Ladki Wale ki Taraf se.webp`, `Ladki Wale Phir se.webp`, `Mother.webp` | Family gallery, in this order |

Tip: GitHub's web uploader accepts files up to 25 MB; larger files (e.g. the video) need GitHub Desktop or `git push`.

## Deploy
1. Push this folder to GitHub (repo root must contain `index.html` and `assets/`).
2. Vercel → Add New Project → import the repo → Framework "Other" → Deploy. Every later push redeploys automatically.
3. After you know your final domain, open `index.html` and change the `og:image` URL (search `og:image`) so WhatsApp shows your logo.

## Edit later (all in `index.html`)
- **Text**: search for the sentence and edit it.
- **Wedding date/time**: search `2027-05-09T17:00:00+05:30` (countdown), and the `09.05.2027` / `MAY` / `09` / `2027` texts.
- **Schedule**: the five `sch-row` lines.
- **Map**: the `<iframe src="https://www.google.com/maps?q=...">` — change the `q=` place name (currently `Bhauwapar, Gorakhpur, Uttar Pradesh`) and the "Open in Google Maps" link.
- **Gallery**: the `data=[ ... ]` list in the script (file name without `.webp`; `fit:'fill'` crops to the frame, `fit:'fit'` shows the whole photo; `pos` sets focus).
- **Photos / music / video**: replace the file in `assets/` keeping the same name.
