# Xwarin — food feed

Kurdish and Iraqi dish data for the [Xwarin](https://github.com/ViperDroid) calorie tracker.

`foods.json` is fetched by the app at launch and layered over the dishes built
into the build, so new and corrected dishes reach phones without a new release.

## Using it

In the app: **Settings → Food updates**, paste this address:

```
https://raw.githubusercontent.com/ViperDroid/xwarin-foods/main/foods.json
```

## Updating

Regenerate from the app repo and replace the file here:

```bash
npm run publish:foods -- 2   # bump the revision each time
```

Raw URLs are cached for about 5 minutes, so an update takes a few minutes to
reach devices.

## Format

```json
{
  "format": "xwarin-foods",
  "version": 1,
  "revision": 1,
  "generated": "2026-07-20T00:00:00.000Z",
  "foods": [ { "id": "yaprax", "name": { "en": "...", "ckb": "...", "ar": "..." }, "per100g": { "kcal": 160, "protein": 5, "carbs": 18, "fat": 7 }, "servings": [] } ]
}
```

Entries are validated on the device. A malformed dish is skipped and counted;
it does not stop the rest of the update. A failed fetch leaves the previously
downloaded dishes in place.

## Data

Dish values are per 100 g, calculated from typical recipes. Portion weights are
estimates until measured. Packaged-product barcodes in the app come from
[Open Food Facts](https://world.openfoodfacts.org) under ODbL 1.0.
