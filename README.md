<p align="center"><img src="icon-500.png" alt="" width="96"></p>
<p align="center"><img src="cover.png" alt="The Philosophy Web" width="100%"></p>

<h1 align="center">The Philosophy Web</h1>
<p align="center"><i>a living map of thinkers, books and influence</i></p>

<p align="center">
 The web · Features · The corpus · Portraits · Architecture · Quick start · Deploy · Support · Credits · License
</p>

---

The Philosophy Web is one structure, not a list. 234 philosophers, from Thales to today, sit in a single
force-directed field and hold each other in place through 478 lines of influence, critique and reply.
Greek, Roman, Chinese, Indian, Japanese, Islamic, Jewish, European, American, African, Caribbean and Latin
American thinkers all share the same field.
Nobody is placed by hand. Where a thinker lands is decided by who shaped them and whom they shaped.

> Plato pulls toward the center because everything leans on him. Stirner sits between Hegel, Feuerbach,
> Marx and Nietzsche because that is where he lived. The layout is the argument.

## The web

- **Nodes** are philosophers. Their size grows with how connected they are.
- **Portraits** sit inside the nodes: 229 of the 234 thinkers have a freely licensed image, and the other five get an initials medallion.
- **Book nodes** (420 of them) can be switched on to hang each thinker's major works around them.
- **Edges** come in three kinds:
  - solid = *influenced*
  - dashed = *critiqued*
  - dotted = *responded to*

Fourteen eras and schools, each with its own ink: `Presocratic`, `Classical Greek`, `Hellenistic & Roman`,
`Eastern`, `Medieval`, `Renaissance & Early Modern`, `Enlightenment`, `German Idealism`, `19th Century`,
`Phenomenology & Existentialism`, `Analytic`, `Political & Conservative`, `Critical Theory & Postwar`,
`Post-structuralism`.

## Features

- D3 v7 force graph with zoom, pan and drag
- Hover a node to light up its neighbours and fade the rest
- Click a node to open a side panel with the portrait and its credit, birth and death (year and place), nationality, schools, a short bio, key ideas, a quote (only where the wording is well attested), major works with years and one-line summaries, a **Start here** reading tip, and every connection in or out
- Search across philosophers and book titles
- Filter by era or school from the dropdown, or toggle eras in the legend
- Toggle book nodes on and off
- Dark parchment-and-ink look with serif type throughout

## The corpus

Content is written as plain text in `src/p*.txt`, one block per thinker:

```
@stirner|Max Stirner|19th Century|1806|Bayreuth|1856|Berlin|German|Young Hegelians, Egoism|Max Stirner
B Max Stirner was the pen name of Johann Kaspar Schmidt...
K Egoism and the unique one; Ideas as spooks; Union of egoists; Ownness over freedom
W The Ego and Its Own|1844|Der Einzige und sein Eigentum; against all fixed ideas.
Q I have set my cause on nothing.
S The Ego and Its Own (Leopold edition)
```

Influence edges are written `source>target type` (`i` = influenced, `c` = critiqued, `r` = responded to) in
`src/edges_new.txt` and `src/old_data.js`. `python3 src/build.py` compiles everything into `data.js`.
To add a thinker, add a block. To add a link, add an edge. The web reorganizes itself.

## Portraits

Each portrait was looked up through the Wikipedia `pageimages` API, with Wikidata P18 as a fallback. Its license
was read from Commons `extmetadata`, and the file was downloaded locally to `portraits/<id>.jpg` at about 400px,
so the site never hotlinks. Every image is public domain or Creative Commons. Author, license and source for all
229 are listed in [CREDITS.md](CREDITS.md). Many portraits of ancient and medieval figures are later artistic
imaginings. Where no portrait exists, the panel says so in a caption (Laozi, Saadia, Judah Halevi, Sextus).

## Architecture

```
philoweb/
├── index.html         # the whole viewer: D3 graph, panel, search, filters, donate modal
├── data.js            # generated: philosophers, books, edges, portrait credits
├── portraits/         # 229 local portraits, ~400px
├── icon-500.png       # emblem / app icon (500x500)
├── favicon.png
├── cover.png          # hero / og image
├── preview.png        # the live graph
├── preview-panel.png  # an open side panel
├── CREDITS.md         # every image's author, license, source
├── src/               # text sources + build.py + portrait fetch scripts
└── README.md
```

There is no build step, no server code and no API key. D3 and the fonts load from CDNs.

## Quick start

```bash
python -m http.server 8000
# open http://localhost:8000
```

Opening `index.html` directly also works.

To rebuild the data after editing `src/`:

```bash
cd src && python3 build.py
```

## Deploy

Drop the folder onto any static host, such as GitHub Pages, Netlify, Vercel or Cloudflare Pages. For GitHub Pages,
push to `main` and turn on Pages in the repo settings, using the root folder.

Website: https://thephilosophyweb.com/

## Support the web

The map is free. Tips keep it growing.

- **SOL:** `G1sH8ermdy5QATeJgDeHNWX48SHojvJEpNECf2a9rERM`
- **ETH:** `0x33A121411C30A4AD0E3416771C0D94B49bFeF570`
- **BTC:** `bc1pntrnksv9cx3ztx45jwsxqrh2900ju22m22y9td82jufllln4d9asnv2y6r`


## Roadmap

- [x] 234 philosophers, 420 books, 478 influence links
- [x] local, freely licensed portraits with full credits
- [x] era filters, search, book toggle
- [ ] still more Islamic, Indian, African and Latin American thinkers
- [ ] timeline mode with nodes laid out by year
- [ ] cite a source for every edge

## Contributing

PRs welcome. Keep everything in `data.js`, keep each summary to one line, and only add influence links that
the thinkers' own writings or standard histories document.

## Credits

Created by Millerman ([@millerman](https://x.com/millerman)). Built with [D3.js](https://d3js.org). Portraits come from Wikimedia Commons under the licenses listed in [CREDITS.md](CREDITS.md).

## License

MIT
