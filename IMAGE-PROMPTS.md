# STATUS

Product photos are now **integrated**: 19 drinks, the hero coffee and 6 pastries were extracted from the supplied reference sheet (cut out, background removed, exported as WebP with transparency).
Files live in `site/images/drinks/` and `site/images/pastries/`; names equal the product ids in the product data.

**Resolution note:** the source sheet is small (each item ~150-250 px), so the cutouts were upscaled ~3x. They look good at card size but will be soft if shown much larger. To upgrade, replace any file with a higher-resolution transparent WebP of the same name (900x1200 for drinks, 900x700 for pastries). No code change is needed.

The rest of this file is the original shot list and prompt guide for re-shooting at higher quality.

---

# ELZORI product photography: shot list and AI prompts

The website loads one transparent image per product from `site/images/drinks/<id>.webp`
(pastries from `site/images/pastries/<name>.webp`). Until a file exists, that product shows
the built-in vector art, so nothing breaks. Drop a file in with the exact name and it appears
automatically. No code change is needed.

## Technical spec (every image)
- Format: WebP with alpha (transparent background). PNG also works if you rename `.png` to `.webp` in `drinkMedia()`.
- Size: 900 x 1200 px (3:4 portrait), drink centred, ~8% empty margin all round. Pastries: 900 x 900.
- Target weight: under 120 KB each (squoosh.app, quality 80).
- Lighting for the whole set: soft warm key light from upper left, faint rim light on the right, neutral reflections, no hard cast shadow (the site adds a floor shadow).
- Same camera height and 35 mm look for all glasses so they sit together in the hero and showcase.

## Shared style prompt (prepend to every drink prompt)
> Photorealistic commercial beverage photograph, isolated product on a pure white seamless background (to be cut out), straight-on eye-level view, soft warm studio lighting, tall clear cylindrical glass with visible thick glass walls, accurate reflections and refraction, crystal-clear ice cubes, fine condensation droplets and subtle water streaks, sharp focus, premium specialty-coffee advertising, 85 mm lens, no text, no logo, no hands, no props, no splashes.

Remove the background with remove.bg / Photoroom / Photopea to get the transparent PNG, then export WebP.

## Drinks (filename = product id)
| File | Prompt (after the shared style prompt) |
|---|---|
| `iced-caramel-latte.webp` | Tall glass, iced caramel latte, cold milk over espresso in distinct layers, golden caramel drizzle running down the inside wall, ice cubes, paper-free glass straw |
| `caramel-macchiato.webp` | Tall glass, layered caramel macchiato: vanilla milk at the bottom, espresso floating on top, crosshatch caramel drizzle, a little foam |
| `iced-americano.webp` | Tall glass, iced americano, dark espresso swirling into clear water, large ice cubes, glossy dark liquid |
| `cappuccino.webp` | Wide white ceramic cappuccino cup and saucer, three-quarter view, thick milk foam with a cocoa-dusted top |
| `cafe-mocha.webp` | Ceramic mug, café mocha with latte art and light chocolate shavings, steam |
| `vanilla-latte.webp` | Tall glass, iced vanilla latte, pale creamy layers over espresso, ice, vanilla bean specks |
| `spanish-latte.webp` | Tall glass, Spanish latte, condensed-milk layer at the bottom, espresso and milk above, ice |
| `white-chocolate-mocha.webp` | Tall glass or mug, white chocolate mocha, ivory milk with espresso, white chocolate drizzle and curls on whipped cream |
| `chocolate-frappe.webp` | Tall glass, thick blended chocolate frappe, whipped cream swirl, chocolate curls, chocolate sauce on the glass wall, straw |
| `caramel-frappe.webp` | Tall glass, blended caramel frappe, whipped cream swirl, caramel drizzle, straw |
| `strawberry-frappe.webp` | Tall glass, pink strawberry frappe, whipped cream, a sliced strawberry on the rim, straw |
| `matcha-latte.webp` | Ceramic cup, matcha latte with a clean leaf latte-art pattern, vivid green |
| `iced-matcha.webp` | Tall glass, iced matcha, green matcha over white milk in layers, ice cubes |
| `cold-brew.webp` | Tall glass, cold brew coffee, deep amber-black liquid, large clear ice cubes, condensation |
| `espresso.webp` | Small white ceramic espresso cup on saucer, thick golden crema |
| `flat-white.webp` | Small ceramic cup, flat white with a tight microfoam heart |
| `affogato.webp` | Clear glass cup, vanilla gelato scoop with espresso poured over it, a little cocoa dust |
| `strawberry-milk.webp` | Tall glass, strawberry milk, pink swirl rising through white milk, ice |
| `signature-elzori-coffee.webp` | Tall elegant glass, the house drink: three layers (espresso, silky milk, caramel foam), a caramel ribbon, one large ice sphere, a thin cocoa dusting |

The remaining menu items use the same file naming (`americano`, `ristretto`, `cafe-au-lait`, `caramel-latte`,
`hazelnut-latte`, `salted-caramel-latte`, `iced-latte`, `mocha-frappe`, `java-chip-frappe`, `vanilla-bean-frappe`,
`cookies-cream-frappe`, `hot-chocolate`, `chai-latte`, `lemon-iced-tea`, plus pastries). They keep the vector fallback until photos are added.

## Pastries (`site/images/pastries/`, 900 x 900, transparent)
`croissant`, `almond`, `muffin`, `cookie`, `cake` (basque cheesecake slice), `roll` (cinnamon roll). Same style prompt, minus glass wording: *photorealistic pastry on a pure white background, soft warm light, 45-degree view*.

## Tools that can generate these
Midjourney, Adobe Firefly, Google Imagen / Gemini, DALL-E, or a food photographer. Keep one tool and one seed style for the whole set so the lighting matches.
