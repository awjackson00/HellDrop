# HellDrop

An unofficial **Helldivers 2 loadout randomizer**. Lock one primary weapon, secondary weapon, or stratagem and randomize a compatible loadout from your owned Warbonds.

## Features

- Guaranteed single-item lock with individual rerolls
- Four unique stratagems, without duplicate backpacks or conflicting permanent support weapons
- Expendable support weapons can accompany a permanent support weapon
- Owned Warbonds and individual gear filtering, saved locally in your browser
- Weapon, armor, booster and stratagem art provided by community catalog sources, with offline fallback visuals
- Mobile-friendly dark military-inspired interface with a custom hellpod/question-mark emblem

## GitHub Pages

This is a static website. It has no build dependencies.

To publish:

1. Open [repository Pages settings](https://github.com/awjackson00/HellDrop/settings/pages).
2. Set **Source** to **Deploy from a branch**.
3. Set **Branch** to `main` and folder to `/(root)`.
4. Click **Save**.

When GitHub Pages finishes deploying, open **https://awjackson00.github.io/HellDrop/**.

To update the site, replace the root `index.html`. GitHub Pages will redeploy automatically when the `main` branch changes.

## Game artwork and data

Images and catalog data are fetched from the community-supported [Helldivers API](https://github.com/DionathaGoulart/Helldivers-api) and the [Helldivers Wiki](https://helldivers.wiki.gg/). An internet connection is needed for live data and most game artwork. If unavailable, a smaller built-in catalog and placeholder artwork are used.

This project is unofficial and is not endorsed by or affiliated with Arrowhead Game Studios or Sony Interactive Entertainment. Game artwork and trademarks belong to their respective owners.

## Troubleshooting deployment

If GitHub Pages displays a 404, visit [Actions](https://github.com/awjackson00/HellDrop/actions) and check that **pages build and deployment** has succeeded. The site is deployed from the `main` branch at `/(root)` and requires `index.html` in the repository root. The project URL preserves repository casing: https://awjackson00.github.io/HellDrop/ .
