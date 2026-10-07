# Brookly — Theme Customizations

## Feature 3: Product page redesign (trikko.co-style)

| File | Change |
|------|--------|
| `sections/main-product.liquid` | Adds the custom styling, two new blocks (**Fit note**, **How it fits**), a **Color swatches → Variant images** setting on the Variant picker block, and a new **"Thumbnails left + stacked scroll"** gallery layout option. |
| `snippets/product-media-gallery.liquid` | New gallery layout: sticky vertical thumbnail rail on the left, all images stacked and scrollable on the right. Clicking a thumbnail scrolls to that image; scrolling highlights the matching thumbnail. Mobile keeps the standard slider. |
| `snippets/product-variant-picker.liquid` | Renders the Color/Colour option as variant-image swatches when the block setting is on. |
| `snippets/product-variant-options.liquid` | Renders each color value as a small photo of that color's variant (falls back to the theme's normal swatches if a color has no variant image). |

**Theme editor setup (Customize → open a product page):**
1. Click the **Product information** section → set **Desktop media layout** to **"Thumbnails left + stacked scroll"** (Media size **Large** recommended).
2. Click the **Variant picker** block → **Color swatches** → **Variant images** (already the default after this update).
3. **Add block → Fit note** — the small "Wrong fit?" text; drag it under the variant picker. Edit the wording freely.
4. In the **Buy buttons** block, keep **"Show dynamic checkout buttons"** checked — that's the Buy now button under Add to cart.
5. **Add block → How it fits** — pick a **video** (autoplays muted on loop) or an **image**, plus an optional heading/text; drag it under the buy buttons.
6. Add **Collapsible row** blocks for the tabs (Description, Shipping, etc.) — they now render with uppercase trikko-style titles.
7. Drag blocks into this order: Title → Price → Variant picker → Fit note → Buy buttons → How it fits → Collapsible rows.

---

## Feature 2: Color swatches on product cards

Product cards show the selected color name with round color dots underneath (selected dot is ringed, hovering a dot previews its name, clicking opens the product with that color selected). A **"Show color swatches"** checkbox in the Product grid section settings toggles them on/off.

| File | Change |
|------|--------|
| `snippets/card-product.liquid` | Renders the color name + swatch dots under the price, with styling and hover behavior included. Colors come from the product's Color/Colour option: it uses the option's swatch (from Shopify's category metafields) when set, otherwise falls back to the color name itself. Shows up to 4 dots plus a "+N" link when there are more. |
| `sections/main-collection-product-grid.liquid` | Adds the **Show color swatches** checkbox (on by default) and passes it to the product cards. |

**Where the toggle is:** Customize → open a collection page → click the **Product grid** section → the **"Show color swatches"** checkbox is under the product card settings (next to "Show second image on hover", etc.).

To show swatches on other product listings too (e.g. Featured collection, Search results), pass `show_color_swatches: true` (or a section setting) to `{% render 'card-product' %}` in those sections the same way.

---

# Feature 1: Mega Menu Collection Images

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
