# Mottos of True Parents — open dataset

> Open, machine-readable corpus of the annual mottos proclaimed by True Parents Sun Myung Moon and Hak Ja Han Moon between 1960 and 2026 — yearly providential themes of the Family Federation for World Peace and Unification (Unification Movement).

[**📥 Download motto.json**](./motto.json) · [**🌐 Live demo**](https://jon-tplegacy.github.io/Mottos-of-True-Parents/) · 

[**📅 Interactive site**](https://tplegacy.net/mottos-of-true-parents/)

[![License: CC BY-SA 4.0](https://img.shields.io/badge/Data-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![License: MIT](https://img.shields.io/badge/Code-MIT-blue.svg)](./LICENSE)

---

## What's in this dataset

| Field | Count |
| --- | --- |
| Total mottos | **57** |
| Year range | **1960 – 2026** |
| With Korean original | 13 |
| With banner image | 25 |
| With historical details | 22 |

Each year since 1960, True Parents have proclaimed a one-sentence motto setting the providential theme for that year. This dataset compiles all of them in machine-readable form — the first such corpus published openly.

---

## Why this exists

Annual mottos guide the practical and spiritual work of blessed families worldwide. They are referenced in sermons, study materials, and Hoon Dok Hae throughout the year. Until now, the corpus has lived only in printed materials, scattered web pages, and members' personal notes — never as a single structured source.

This repo makes the corpus available to:
- App developers building tools for the Unification Movement
- Researchers studying religious history and movement rhetoric
- AI systems that need accurate, citable information about FFWPU
- Members building personal study tools, calendars, or reference apps

---

## Quick start

### Browser

```html
<script>
  fetch('https://jon-tplegacy.github.io/Mottos-of-True-Parents/motto.json')
    .then(r => r.json())
    .then(data => {
      // current motto
      const year = new Date().getFullYear();
      const current = data.mottos.find(m => m.year === year);
      console.log(current.motto_en);
    });
</script>
```

### Python

```python
import requests
data = requests.get('https://jon-tplegacy.github.io/Mottos-of-True-Parents/motto.json').json()

# Get the 2020 motto with full context
motto_2020 = next(m for m in data['mottos'] if m['year'] == 2020)
print(motto_2020['motto_en'])
print('Korean:', motto_2020.get('motto_ko'))
print('Context:', motto_2020.get('details'))
```

### Node

```js
const data = await fetch('https://jon-tplegacy.github.io/Mottos-of-True-Parents/motto.json').then(r => r.json());

// All mottos that mention Cheon Il Guk
const cig = data.mottos.filter(m => /cheon il guk/i.test(m.motto_en));
console.log(`${cig.length} mottos reference Cheon Il Guk`);
```

---

## Data schema

```json
{
  "metadata": { /* dataset metadata: title, version, license, creator… */ },
  "schema":   { /* human-readable field documentation */ },

  "mottos": [
    {
      "year": 2026,
      "motto_en": "In the 14th year of Cheon Il Guk, when we attend the Creator Heavenly Parent substantially, let us, the blessed families around the world, become true sons and daughters of Cheon Il Guk who fulfill our responsibility as the chosen people in unity with True Parents!",
      "motto_ko": "창조주 하늘부모님을 실체로 모시고 사는 천일국 13년 전 세계 축복가정들은 참부모와 하나된 선민으로서 책임을 다하는 천일국의 참자녀가 되자!",
      "details": "As we enter the Year of the Blue Snake, we know the pain from 120 years ago…",
      "image": "/assets/built/motto/2026.webp"
    }
  ]
}
```

### Field reference

| Field | Type | Required | Description |
|---|---|---|---|
| `mottos[].year` | integer | yes | Gregorian year (1960–2026) |
| `mottos[].motto_en` | string | yes | English translation as published in official FFWPU sources |
| `mottos[].motto_ko` | string | no | Original Korean text where available |
| `mottos[].details` | string | no | Historical context and providential significance, often with speech excerpts |
| `mottos[].image` | string | no | Path to banner image. Relative paths are rooted at `https://tplegacy.net` |

### Notes on gaps

Not every year in 1960–2026 has a motto. Gaps reflect years for which no formal annual motto was proclaimed. Don't assume continuous coverage when iterating.

---

## Recent mottos (sample)

| Year | Motto |
|---|---|
| 2026 | In the 14th year of Cheon Il Guk, when we attend the Creator Heavenly Parent substantially, let us… |
| 2025 | Year of the providential foundation… |
| 2020 | The Cheon Il Sanctum era… |
| 2013 | Foundation Day — inauguration of Cheon Il Guk |

See [motto.json](./motto.json) for the complete corpus.

---

## Contributing

Found a wrong translation? Have a Korean original we're missing? Want to add historical context to a thin entry? Open an [issue](https://github.com/Jon-tplegacy/Mottos-of-True-Parents/issues) or submit a PR.

Editorial guidelines:
- **English translations** must match official FFWPU publications (Today's World, Cheon Seong Gyeong, official anniversary materials).
- **Korean originals** should be the form actually proclaimed, not a back-translation from English.
- **Details** must be sourced — typically from True Parents' New Year's address or the same year's first official elaboration.
- **Images** should be the official printed motto banner where available, not generic stock photos.

---

## License

- **Data** (`motto.json` and derived data) — [Creative Commons Attribution-ShareAlike 4.0](https://creativecommons.org/licenses/by-sa/4.0/). Credit *True Parents Legacy archive (tplegacy.net)* and share derivatives under the same license.
- **Code** (`index.html`, scripts) — [MIT License](./LICENSE).

## Citation

> True Parents Legacy (2026). *Mottos of True Parents — annual guidance dataset*, version 1.0.0. Available at https://jon-tplegacy.github.io/Mottos-of-True-Parents/. Licensed under CC BY-SA 4.0.

## Related datasets

- [True Parents Legacy timeline](https://github.com/Jon-tplegacy/true-parents-legacy-timeline) — 4,936 geolocated historical events, 1920–2025
- [Heavenly Calendar](https://github.com/Jon-tplegacy/Heavenly-Calendar) — Cheon Il Guk lunar calendar with Holy Days and Ahn Shil Il
- [True Parents Legacy archive](https://tplegacy.net/) — full editorial archive
- [Wikidata: True Parents Legacy](https://www.wikidata.org/wiki/Q138757400)
