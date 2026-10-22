# Underworld Crusaders

A responsive, bilingual landing page for Alexander “Kraziman” Tanchev and the Underworld Crusaders gaming community. It brings together the Twitch stream, personal introduction, social links, and Discord community in a retro-inspired design.

## Features

- Bulgarian and English translations, with Bulgarian as the default and language preference saved in `localStorage` when available.
- Click-to-load Twitch player for the `notkraziman` channel.
- Links to the community’s links hub and Discord invite.
- Confirmation dialog for ordinary clicks on Twitch and Discord links; confirmed destinations open in a new tab.
- Responsive layouts, with desktop navigation appearing at widths of 900px and above.
- Animated lettering, a scrolling ticker, a grid floor, floating pixels, and scroll reveals.
- Keyboard focus indicators, portrait alternative text, and support for reduced-motion preferences.

## Technology

Plain HTML, CSS, and JavaScript in a single HTML document. No package installation, framework, build step, or application backend is required. Google Fonts supplies **Pirata One** and **Rubik**, with local font fallbacks.

## Files

Save the supplied HTML as `index.html` and place its referenced images alongside it:

```text
.
├── index.html
├── founder.jpg
├── favicon.png
├── apple-touch-icon.png
└── README.md
```

The image files are referenced by the HTML and must be supplied separately. The portrait declares an 800 × 800 image size and displays with a square crop.

## Run locally

Open `index.html` in a modern browser to preview the page. For HTTP-based testing, run a static server from the project folder. For example, if Python is installed:

```sh
python -m http.server 8000
```

Then visit <http://localhost:8000>.

Internet access is required for Google Fonts, the Twitch player, and external destinations. Test the Twitch embed on the deployed HTTPS site as well; a local file preview does not establish that the embed will work in production.

## Customize

| Item | Location in `index.html` |
| --- | --- |
| Translated text | `STRINGS.bg` and `STRINGS.en` |
| Translated elements | `data-i18n` attributes |
| Colors | CSS custom properties in `:root` |
| Portrait and icons | `founder.jpg`, `favicon.png`, and `apple-touch-icon.png` references |
| Twitch channel | Twitch links, player label, iframe URL, and iframe title |
| Social links hub | Links to `https://links.underworldcrusaders.org` |
| Discord destination | Link to `https://discord.underworldcrusaders.org` |
| Search and sharing metadata | `<title>`, description, and Open Graph tags in `<head>` |
| Copyright | Footer text |

Add translation keys to both dictionaries and attach the corresponding `data-i18n` attribute to new translated elements. The language switch updates these elements, the document language, the page title, and ticker text. The description metadata, navigation accessibility label, portrait alternative text, and iframe title remain as written in the HTML.

Links carrying `data-site` use the leave-page confirmation dialog when supported by the browser. The links hub opens directly. Modified clicks retain normal browser behavior.

## Deploy

Upload `index.html` and the image assets to an HTTPS static web host, preserving their relative paths. No server-side runtime is needed.

The Twitch iframe derives its `parent` query parameter from `location.hostname`, so it uses the hostname serving the page. Verify playback on each production hostname.

Before publishing:

- Replace `og:image` with the absolute URL of an actual share-preview image; the supplied value points to the site root.
- Confirm the portrait and icons load correctly.
- Check both languages, mobile and desktop layouts, keyboard navigation, reduced-motion behavior, and the external-link dialog.
- Verify Twitch playback and the links hub and Discord destinations.

## External services and storage

Google Fonts is requested when the page loads. The Twitch iframe is created only after the visitor presses the player button. The selected language is stored under the `lang` key in browser `localStorage`, when storage is available. The supplied code contains no analytics integration.

## License

No license was included with the supplied source. Add a `LICENSE` file to define permitted reuse and ensure you have permission to use the included images and branding.
