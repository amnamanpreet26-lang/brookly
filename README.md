# Brookly — Mega Menu Collection Images

Adds featured-collection images (image + title) to every mega menu in the header, configurable per menu item from the theme editor. The same images also show in the mobile menu drawer, which opens a single panel per menu item (arneclo.com-style) instead of nested dropdowns.

## Files changed

| File | Change |
|------|--------|
| `sections/header.liquid` | Adds a new **"Mega menu collections"** block to the Header section schema (and raises `max_blocks` to 15 so you can add one block per menu item). |
| `snippets/header-mega-menu.liquid` | Renders the selected collections (featured image + title) on the right side of the matching mega menu. Also force-hides the desktop mega menu below 990px so it never appears on mobile. |
| `snippets/header-drawer.liquid` | Mobile drawer: tapping a top-level item opens **one single panel** — child items with sub-links become bold headings with their links listed flat underneath (no second-level dropdowns) — followed by the same collection image cards in a swipeable row. |
| `snippets/menu-collection-cards.liquid` | New shared snippet that renders the collection cards for both the desktop mega menu and the mobile drawer, from the same blocks. |

## How to install

In Shopify admin: **Online Store → Themes → ⋯ → Edit code**, then:

1. Open `sections/header.liquid`, replace its contents with the file from this repo, and save.
2. Open `snippets/header-mega-menu.liquid`, replace its contents with the file from this repo, and save.
3. Open `snippets/header-drawer.liquid`, replace its contents with the file from this repo, and save. (If your drawer file has custom changes, back it up first.)
4. Under **Snippets**, click **Add a new snippet**, name it `menu-collection-cards`, paste the file from this repo, and save.

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
- One "Mega menu collections" block configures both desktop and mobile — no separate mobile setup needed.
- On mobile, the desktop mega menu is hidden; only the hamburger drawer shows. Each top-level item opens exactly one panel (no nested dropdowns inside).
- If two blocks target the same menu item, the first one wins.
- `snippets/header-drawer.liquid` here is based on the standard Dawn drawer. If your theme's drawer was customized, compare before replacing.
