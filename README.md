# turtle-theme

A HubSpot CMS theme built for the CMS for Developers II practicum. It is a Teenage Mutant Ninja Turtles–themed site with a header, footer, a banner section, and a "Turtle Team" module, built on the HubSpot CMS theme structure (`theme.json`, `fields.json`, templates, sections, and modules).

**Live site:** https://cms-for-developers-ii-7768984.hs-sites.com/

## Project structure

```
turtle-theme/
├── theme.json                  # Theme settings (label, author, global options)
├── fields.json                 # Theme-level fields: global colors, header and footer backgrounds
├── templates/
│   ├── layouts/base.html       # Base layout: <head>, CSS/JS includes, header/footer, main block
│   ├── page.html               # Page template with two drag-and-drop areas
│   └── partials/
│       ├── header.html         # Global header (skip link + main navigation)
│       └── footer.html         # Global footer
├── sections/
│   ├── banner-text-image.html  # Top banner: image and text, responsive columns
│   ├── turtle-team.html        # Section wrapping the "team" module
│   └── sample-section.html     # Unused sample section (not available for new content)
├── modules/
│   └── team.module/            # "Turtle Team" module (HTML, CSS, JS, fields, meta)
├── css/
│   ├── main.css                # Main stylesheet, loaded from base.html
│   ├── layout.css              # Fluid 12-column grid (based on the HubSpot boilerplate)
│   └── fonts.css               # Font definitions
├── js/
│   └── main.js                 # Theme JavaScript, loaded in the footer
└── images/                     # Theme images and section/module preview screenshots
```

## How it works

- **Base layout** (`templates/layouts/base.html`) loads `css/main.css` in the `<head>` and `js/main.js` in the footer, then renders the global header and footer partials around the page body.
- **Page template** (`templates/page.html`) extends the base layout and provides two drag-and-drop areas: `top section` (the banner) and `main body section` (the team section). Editors can add, remove, and reorder sections in these areas in the HubSpot page editor.
- **Sections** are drag-and-drop sections built from `dnd_section` and `dnd_column` tags. They can be inserted into any page that allows them.
- **Modules** are drag-and-drop components with their own `fields.json` (editable options) and `meta.json` (module ID, label, and where it can be used). The `team` module is placed by `sections/turtle-team.html`.
- **Global colors** are set in `fields.json` as Primary, Secondary, and Tertiary. They drive the header and footer backgrounds and inherit from the brand settings where available.

## Getting started

There is no build step or local starting script. The theme is uploaded to HubSpot and edited there.

1. Make sure you have access to the HubSpot account that hosts the CMS for Developers II site.
2. Upload or sync the `turtle-theme` folder to Design Manager (for example, with the HubSpot CLI: `hs upload turtle-theme turtle-theme`, or via the Design Manager file browser).
3. Open the live site or create a new page using the `page.html` template to see the theme in use.
4. After changing a file locally, re-upload it to HubSpot and refresh the page to see the change.

## Notes

- `sections/sample-section.html` and the `team.module` path it references are for reference only. The active team section is `sections/turtle-team.html`.
- The header navigation links point to in-page anchors (`#maincontent`, `#turtles`). Add matching `id`s to the page content so they scroll to the right place.
- `images/` contains preview screenshots referenced by the templates and sections (`screenshotPath`). Keep them in place so the Design Manager previews still work.

## Credits

Built by David Leonard-Scully as part of the CMS for Developers II practicum. The layout grid and base template are adapted from the [HubSpot CMS theme boilerplate](https://github.com/HubSpot/cms-theme-boilerplate).
