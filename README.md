# BC Bible — Study Data Repository

This repository contains downloadable study data packages for the **Biblical Context Bible (BC Bible)** app.

## Structure

```
releases/
  v1.0.0/
    genesis_ch1_ch2.json   — Genesis chapters 1–2 (verses, words, lexicon)
    data.json              — Combined data file for app update import
```

## How it works

BC Bible checks the GitHub Releases API for new data packages. When a new release is published, users are notified in the app's **Settings → Data & Updates** screen and can download the package directly.

## Data format

Each release asset is a JSON file with top-level keys matching database table names:

```json
{
  "chapters":         [ {...}, ... ],
  "verse_headings":   [ {...}, ... ],
  "verses":           [ {...}, ... ],
  "words":            [ {...}, ... ],
  "lexical_entries":  [ {...}, ... ],
  "root_words":       [ {...}, ... ],
  "word_occurrences": [ {...}, ... ],
  "cross_references": [ {...}, ... ]
}
```

The app merges incoming rows using `INSERT OR REPLACE`, so updates are safe to re-apply.

## Releasing data

1. Build your JSON data file following the schema above.
2. Create a GitHub Release with a tag like `v1.1.0`.
3. Attach the `.json` or `.zip` (containing the JSON) as a release asset.
4. Users will see the update the next time they check for updates in the app.
