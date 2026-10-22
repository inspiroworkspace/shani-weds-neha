# How to change anything on the website

Everything lives in **two places**:
- `index.html` – all text, dates, layout, scripts
- `assets/` – photos, video, music

**Golden rule:** to replace a photo/video/music, upload a new file with the **exact same name** (GitHub → `assets` → *Add file → Upload files*, tick "Commit directly to main"). Vercel redeploys automatically in ~1 minute.

To edit text on GitHub: open `index.html` → pencil icon (✏️) → press **Ctrl+F** (Cmd+F on Mac) and search for the words you want to change → edit → **Commit changes**.

---

## 1. Text you may want to change

| What | Search for (Ctrl+F) |
|---|---|
| Browser tab title | `<title>` |
| Names on top | `class="names hl"` (Shani / Neha) |
| Date under "Wedding" | `09.05.2027` |
| Blessing lines | `Two Souls` |
| Invitation paragraph | `Join us for an evening` |
| Heading above the cards | `The Celebration begins` |
| Schedule times & events | `sch-row` (five lines: time and event name) |
| Location text | `Bhauwapar, Gorakhpur,` |
| Dress Code / Gift text | `Wear anything you like` and `Whether you come or not` |
| Celebrate With Us text | `Come with love` |
| Family button text | `Click to See Who` |
| Gallery heading | `Our family member` |
| Closing words | `Hope to see you there` |

## 2. Wedding date, time and cards
- **Countdown target:** search `2027-05-09T17:00:00+05:30` → format is `YYYY-MM-DDTHH:MM:SS+05:30` (24-hour, India time).
- **Cards:** search `data-v="MAY"`, `data-v="09"`, `data-v="2027"` and change the matching `<span>MAY</span>` etc. next to each.
- **Hero date:** search `09.05.2027`.

## 3. Schedule
Each line looks like  
`<div class="sch-row"><div class="t">5 PM</div><div class="dot"></div><div class="n">Preparation</div></div>`  
Change `5 PM` (time) and `Preparation` (event). Copy a whole line to add an event, delete a line to remove one.

## 4. Map / venue
Search `google.com/maps?q=`. Replace the words after `q=` (use `+` for spaces), e.g. `q=Shiv+Mandir,+Bhauwapar,+Gorakhpur`.  
Also update the "Open in Google Maps" link: search `maps/search/?api=1&amp;query=`.
Tip: in Google Maps, search your venue → Share → *Embed a map* shows the exact name to use.

## 5. Photos, video, music (same-name replacement)
| File in `assets/` | What it is |
|---|---|
| `first seal.webp` | Opening cover (envelope) |
| `Intro Final.mp4` | Intro video – plays fully, has sound, can't be skipped |
| `bg-music.mp3` | Background music (loops) |
| `om ganehya namah.webp` | Ganesh artwork in the invitation card |
| `neha shani.webp` | Closing couple photo |
| `guest.webp` | Wax-seal button that opens the family gallery |
| `Aryan`, `Musu`, `Sanjana`, `Papa`, `Ladki Wale ki Taraf se`, `Ladki Wale Phir se`, `Mother` (`.webp`) | Family gallery |

**Keep photos light (fast loading):** resize to about **1400 px on the long side** and compress to **under 150 KB** before uploading – free tool: https://squoosh.app (choose WebP, quality ~75). Phone photos straight from the camera are 5–10 MB and will make the page slow.

**Video tips:** vertical 9:16, ideally under 10 MB. Compress free at https://www.freeconvert.com/video-compressor (H.264 MP4).

## 6. Family gallery – add / remove / reorder people
In `index.html` search `EDIT HERE`. You'll see:
```js
{f:'Aryan',fit:'fill'},
{f:'Musu',fit:'fill',pos:'left center'},
{f:'Ladki Wale ki Taraf se',fit:'fit'},
```
- `f` = file name (without `.webp`) and also the caption shown under the photo.
- `fit:'fill'` fills the frame (crops). `fit:'fit'` shows the whole photo (best for group photos).
- `pos:'left center'` moves the focus point when cropping (`left`, `right`, `top`, `bottom`, `center`).
- Order of lines = order in the gallery. Add a line = add a person (upload `Name.webp` too). The gallery loops automatically.
- Speed of auto-slide: search `4800` (milliseconds). Turn auto-slide off: search `startAuto()` inside the click handler and delete `setTimeout(startAuto,3500)`.

## 7. Colours and fonts
At the top of the `<style>` block (search `:root{`):  
`--gold` heading colour · `--brown` body text · `--bg` page background.  
Fonts are in `assets/fonts/` – don't delete them.

## 8. WhatsApp preview + tab icon
Search `og:image` (preview image) and `rel="icon"` (tab icon). Both currently use  
`https://res.cloudinary.com/j3mlf6f3/image/upload/Inspiro-Workspace-Logo.webp`.  
Replace that link with any public image link (best preview: 1200×630 JPG/PNG under 300 KB). WhatsApp caches previews – to refresh, add `?v=2` after the link or share it again after a day.

## 9. If something breaks
GitHub → **Commits** → click the last good commit → **Browse files**, or on the commit press **Revert**. Vercel → *Deployments* → three dots on an older deployment → **Promote to Production**. Never delete `index.html` or the `assets` folder.

## 10. Testing locally (optional)
Open a terminal in the folder and run `python -m http.server 8000`, then visit http://localhost:8000
