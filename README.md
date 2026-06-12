# Email Signature Generator

A client-side email signature generator for Kellenberg Memorial High School faculty and staff.

## Features

- Logo toggle: 40th Anniversary logo (default) or School Seal
- School and clergy titles (Mr., Mrs., Miss, Ms., Dr., Bro., Fr., Dcn.)
- Optional credentials field
- Optional extension on the main line (516) 292-0200
- Auto-includes kellenberg.org and social media icons (Facebook, Instagram, YouTube)
- Logo links to kellenberg.org in the signature
- One-click copy to clipboard
- Live preview
- Gmail setup instructions built into the page

## Hosting

The page is a single self-contained `index.html`. It is intended to live on the school's internal Google Site, either:

1. **Embed by URL**: host `index.html` anywhere (Render static site, GitHub Pages on a public repo, etc.), then in Google Sites use Insert > Embed > By URL.
2. **Link out**: host it the same way and link to it from the Site.

Pasting the full file into an Embed code block also works if it stays under the embed size limit.

Note: some Google Sites embeds block clipboard access inside the iframe. The page's fallback note links users to open it in its own tab, but test the Copy button in the embedded context before rollout.

## Image hosting (important)

Gmail strips base64/data-URI images from signatures, so every image in the signature must be a public HTTPS URL. All logos and social icons are hosted in the public assets repo:

`https://github.com/harnischllc/kellenberg-signature-assets`

referenced via `raw.githubusercontent.com` URLs. Keep that repo public or signature images will break in recipients' inboxes.

## Configuration

The `CONFIG` object at the top of the `<script>` section in `index.html` contains:

- Logo URLs and display widths (40th Anniversary and School Seal)
- Phone, address
- Website URL
- Social media links and icon URLs
- Brand colors

Hosted assets: `KM40th.png` (40th Anniversary, displays 110px wide), `KMHSseal.png` (seal, displays 80px wide), `KMfirebird.png` (KM athletic mark, spare), and the three social icons. All are trimmed and saved at 2x display size for retina.

## Customization

### Titles/Honorifics

Edit the `<select id="honorific">` dropdown in the HTML.

### Colors

CSS variables at the top of the `<style>` block:

- `--primary`: #2c3e94 (Kellenberg blue)
- `--primary-hover`: #4359c7 (link/button hover)
- `--gold`: #ffba00

The signature itself uses `CONFIG.primaryColor` and `CONFIG.goldColor`.

### Social Icons

Icons are 80x80 PNGs in Kellenberg blue (#2c3e94), displayed at 20x20, hosted in the assets repo. To change them, update the `CONFIG.socials` icon URLs.

## Browser Support

Works in all modern browsers. Uses Clipboard API with fallback for older browsers.
