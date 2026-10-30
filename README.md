# Bad MOPHO

Web MIDI editor and librarian for the Dave Smith Instruments Mopho synthesizer.

**Use it online:** https://xc3n.github.io/BadMOPHO/
**Use it offline:** download `bad-mopho.html` from the site (or build it, below) and open it in Chrome.

## Layout

```
bad-mopho.html     the tool
common/            shared code: a pinned copy from XC3N/webtools (see common/PINNED.json)
build.js           inlines includes → dist/bad-mopho.html (+ dist/index.html)
sync-common.js     refreshes common/ from a local clone of XC3N/webtools
.github/workflows  builds and publishes dist/ to GitHub Pages on every push to main
```

History before this repository (October 2026 and earlier) is in [XC3N/webtools](https://github.com/XC3N/webtools); the commits for Bad MOPHO were carried over here.

## Building

```
node build.js
```

Node 18+, no dependencies. Output goes to `dist/` (not committed — GitHub Actions builds it).
The source includes shared files with `/* @include common/file.js */`.

## Shared code

`common/` is copied from [XC3N/webtools](https://github.com/XC3N/webtools), pinned to the commit in `common/PINNED.json`, so a change there never changes Bad MOPHO by itself. To take a newer version:

```
node sync-common.js ../webtools --check   # what would change
node sync-common.js ../webtools           # copy it and update the pin
```

Then review `git diff common/`, build, check the tool and commit. Changes to the shared code itself are made in webtools first, then synced here.

## Credits

UX & features design by XC3N · implementation & coding by Claude. Interface typefaces: Instrument Sans and JetBrains Mono, from Google Fonts (SIL Open Font License).

If this editor is useful to you, consider supporting the music at [xc3n.bandcamp.com](https://xc3n.bandcamp.com).

## Licence

[MIT](LICENSE.md), the shared code in `common/` included. The name "Bad MOPHO" and its logo aren't covered — forks need their own name. See [TRADEMARKS.md](TRADEMARKS.md).
