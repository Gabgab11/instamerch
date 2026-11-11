# InstaMerch

Upload a logo, see it on 12 products, pick what you want, order, and track it. The InstaMerch team moves each order through production, and the customer gets an email at every step.

This is a **clickable front-end prototype**: one self-contained `index.html`, no build step and no backend. Data lives in memory and resets on reload.

## Run it

Open `index.html` in a browser, or serve the folder:

```bash
npx serve .
```

To publish with GitHub Pages: **Settings → Pages → Deploy from branch → `main` / root**.

## What's in it

**Customer side**
- Sign in / create account (demo: any email and an 8+ character password).
- Onboarding: what the merch is for, then logo upload.
- **Real logo upload** (PNG, JPG, SVG up to 10 MB):
  - white or light solid backgrounds are removed automatically
  - empty space around the artwork is cropped so the logo fills each print area
  - SVGs are cleaned (scripts and event handlers stripped) and auto-cropped
  - low-resolution files get a warning
- **Smart logo versions** per product: full color on light products; on dark products, dark logos switch to a light version and colorful logos stay in full color; one-tone version for laser engraving; embroidery labels.
- **Runway**: 3D turning stage of 12 pieces with drag/swipe, autoplay with a progress bar, keyboard arrows, a custom cursor on desktop and a close-up view with numbered detail pins.
- **All 12 lineup**: every piece at once, switchable between the colors you set, light colors and dark colors.
- Per piece: 4–20 stock colors plus a custom color picker, print placement, logo size with a safe-area warning, sizes and quantities.
- Order and checkout with bulk discounts, regional shipping and a test-mode card; confirmation; order tracking with timeline, email preview and reorder.

**Team side** (the "Team" tab)
- Orders queue with status filters and stats (open orders, revenue, average fulfillment time, top product).
- Order detail: one-tap status changes that queue a branded email to the customer, optional note, carrier and tracking number, hold with reason (admins only), assignee, internal notes, history log with who and when, email log with resend, and print specs per item.
- Catalog and pricing: base prices and bulk discount tiers.
- Role switch: Admin vs production staff.

## Brand

The logo is the "Placed" wordmark: lowercase **instamerch** in Inter Tight SemiBold (outlined), with the dot on the i as a tilted Signal Orange square. Files live in `brand/`:

- `instamerch-logo-color.svg`, `-black.svg`, `-white.svg`, `-reversed-color.svg`
- `instamerch-icon-light.svg`, `-dark.svg`, `-orange.svg`, plus `favicon-32.png`, `apple-touch-icon.png`, `icon-512.png`
- `InstaMerch-Logo-HD.pdf`: vector logo sheet with colours and usage

Colours: Ink `#151413`, Signal Orange `#E8501E`, Stone `#F1F0EC`.

**Intro animation:** on first visit in a session, the "i" hops onto a white screen, then "nstamerch" pops up letter by letter and the page fades in (about 4.5 s). Click or press Esc to skip. It's skipped when the visitor has reduced motion turned on. It's the `im-intro` markup at the top of `<body>` with its styles in `<head>`; to replay it, clear the `im-intro-seen` key from session storage.

## Products

Classic tee, pullover hoodie, dad cap, canvas tote, daypack, ceramic mug, steel bottle, travel tumbler, hardcover notebook, phone case, die-cut sticker and framed print. Products are drawn as shaded SVGs with a defined print area per placement, so the renderer can later be swapped for photo mockups.

Prices, the sample "Northfield Coffee" logo and example orders are placeholders.

## Next step: the real app

Suggested stack: Next.js + TypeScript, Tailwind, PostgreSQL with Prisma (Users, Designs, Products, Variants, PrintAreas, Orders, OrderItems, OrderStatusHistory, Notifications), S3-compatible storage for uploads, Stripe Checkout, Resend for transactional email with a queue and retries.
