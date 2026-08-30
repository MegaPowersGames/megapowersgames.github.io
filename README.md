# megapowersgames.github.io

The Mega Power Games landing page. One static HTML file, no build step, no dependencies.

Served at `https://megapowersgames.github.io` once published. This is the URL the
RDC business card QR code encodes.

## Contents

| Path | What it is |
|---|---|
| `index.html` | The entire page. Inline CSS, no JavaScript. |
| `img/logo-studio.png` | Studio logo, resized to 700px wide. |
| `img/logo-game.png` | Survive the Horde logo, resized to 800px wide. |
| `img/shot-*.jpg` | Game screenshots, resized to 1600px and re-encoded as JPEG. |
| `img/sizzle.mp4` | The 10 second sizzle, re-encoded to 1280x720 (~4.7 MB from 47 MB). |

Originals live in `RDC Demo Day Assets/`. They are 5–11 MB PNGs and a 47 MB MP4,
far too heavy to serve directly, so everything here is a derived copy.

## Publishing

1. Create a **public** repo named exactly `megapowersgames.github.io` under the
   `MegaPowersGames` org. The name must match the org name — that is what makes it
   an organisation Pages site served from the root URL.
2. Push this folder to the default branch.
3. In the repo's Settings → Pages, set the source to that branch, root folder.
4. Wait a minute or two, then load `https://megapowersgames.github.io`.

The repo must be public. GitHub Pages on a private repo requires a paid plan.

## Before it goes live

One claim is worth revisiting: the headline says "tens of millions of downloads".
That is defensible from Solitaire's 10M+ Android installs plus the rest of the
portfolio. If Kyler pulls a higher verified figure, state it exactly instead.

## If you buy a domain later

Do not rely on GitHub redirecting `megapowersgames.github.io` to a custom domain —
that behaviour is not documented and the printed QR code depends on it. Instead,
keep this repo serving a page you control and forward it yourself:

```html
<meta http-equiv="refresh" content="0; url=https://megapowergames.com">
```

That way the printed QR keeps working regardless of what GitHub does.

## Editing

Open `index.html` in any editor. There is no build, no package manager, and no
framework. To re-derive an image or the video from a new original:

```bash
sips -Z 1600 -s format jpeg -s formatOptions 80 SOURCE.png --out img/shot-name.jpg
```

```bash
ffmpeg -i SOURCE.mp4 -vf "scale=1280:-2" -c:v libx264 -crf 30 -preset slow -pix_fmt yuv420p -c:a aac -b:a 96k -movflags +faststart img/sizzle.mp4
```
