# Brookly — Mega Menu Collection Images

Adds featured-collection images (image + title) to every mega menu in the header, configurable per menu item from the theme editor.

## Files changed

| File | Change |
|------|--------|
| `sections/header.liquid` | Adds a new **"Mega menu collections"** block to the Header section schema (and raises `max_blocks` to 15 so you can add one block per menu item). |
| `snippets/header-mega-menu.liquid` | Renders the selected collections (featured image + title) on the right side of the matching mega menu, with styling included. |

## How to install

In Shopify admin: **Online Store → Themes → ⋯ → Edit code**, then:

1. Open `sections/header.liquid`, replace its contents with the file from this repo, and save.
2. Open `snippets/header-mega-menu.liquid`, replace its contents with the file from this repo, and save.

## Where to find the options (theme editor)

1. Go to **Online Store → Themes → Customize**.
2. Click the **Header** section in the left sidebar.
3. Click **Add block → Mega menu collections**.
4. In the block settings:
   - **Menu item title** — type the top-level menu item's name exactly as it appears in your main menu (e.g. `Mens`). Spelling matters, capitalization doesn't.
   - **Collections** — pick up to 4 collections. Each one shows its featured image with its title underneath, linking to the collection.
5. Repeat steps 3–4 for every mega menu (one block per top-level menu item: `Mens`, `Womens`, etc.).
6. Save.

## Notes

- Requires the header's **Desktop menu type** to be set to **Mega menu**, and images only appear for menu items that have sub-links (that's what makes a mega menu open).
- The image shown is the collection's **featured image** (set on the collection in admin). If a collection has no image, Shopify falls back to its first product's image; if there's neither, a placeholder is shown.
- The mega menu is desktop-only (as in Dawn); the mobile drawer menu is unchanged.
- If two blocks target the same menu item, the first one wins.
