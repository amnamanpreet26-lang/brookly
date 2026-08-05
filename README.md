# Brookly — Mega Menu Collection Images

Adds featured-collection images (image + title) to every mega menu in the header, configurable per menu item from the theme editor. The same images also show in the mobile menu drawer, which opens a single panel per menu item (arneclo.com-style) instead of nested dropdowns.

## Files changed

| File | Change |
|------|--------|
| `sections/header.liquid` | Adds a **"Mega menu collections"** block (desktop, one per menu item) and a **"Mobile menu images"** setting (a single set of up to 3 collections for the mobile drawer). |
| `snippets/header-mega-menu.liquid` | Renders the selected collections (featured image + title) on the right side of the matching mega menu. Also force-hides the desktop mega menu below 990px so it never appears on mobile. |
| `snippets/header-drawer.liquid` | Mobile drawer: tapping a top-level item opens **one single panel** — child items with sub-links become bold headings with their links listed flat underneath (no second-level dropdowns). Three collection images (from "Mobile menu images") show at the very bottom of the drawer menu. |
| `snippets/menu-collection-cards.liquid` | Shared snippet that renders the collection cards for the desktop mega menu. |

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

### Mobile menu images (3 images at the bottom of the drawer)

1. In the theme editor, click the **Header** section itself (not a block).
2. Scroll to **Mobile menu images** and click **Select collections** — pick up to 3.
3. Save. They appear side by side at the very bottom of the mobile menu, under all menu items.

## Notes

- Requires the header's **Desktop menu type** to be set to **Mega menu**, and images only appear for menu items that have sub-links (that's what makes a mega menu open).
- The image shown is the collection's **featured image** (set on the collection in admin). If a collection has no image, Shopify falls back to its first product's image; if there's neither, a placeholder is shown.
- Desktop and mobile are configured separately: "Mega menu collections" blocks control the desktop mega menus (per menu item); the "Mobile menu images" setting controls the 3 images at the bottom of the mobile drawer.
- On mobile, the desktop mega menu is hidden; only the hamburger drawer shows. Each top-level item opens exactly one panel (no nested dropdowns inside), with no images inside the panels.
- If two blocks target the same menu item, the first one wins.
- `snippets/header-drawer.liquid` here is based on the standard Dawn drawer. If your theme's drawer was customized, compare before replacing.
