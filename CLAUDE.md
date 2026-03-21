# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this project is

A Hugo-based website for accordion/bayan sheet music and chord transcriptions, published at `imelnikov.ru/music`. Content is in Russian. Songs are organized by artist in `content/<artist>/`.

## Commands

```bash
# Run local dev server
hugo server

# Create new content page
hugo new content content/<artist>/<song-slug>.md

# Build static site
hugo
```

## Content structure

Each song is a Markdown file with frontmatter. Two main frontmatter patterns are used:

**Simple page** (most songs):
```yaml
layout: page-single.html
```

**Page with ABC notation** (renders sheet music via abcjs):
```yaml
layout: page-single.html
chords: |
    X:1
    T:Song Title
    K:C
    "Am" A| ...
```

The `chords` field contains ABC notation which is rendered by `static/abcjs_basic_5.10.3-min.js`.

## Theme

Uses the [Ananke](https://github.com/theNewDynamic/gohugo-theme-ananke) theme, installed as a git submodule at `themes/ananke`.

## Song content format

Song pages typically contain some combination of:
- Chord progressions (in code blocks)
- Solo/melody note sequences (letter notation like `A B C D`)
- YouTube links for reference recordings
- Tags like `*гармонь*, *баян*, *разбор*, *ноты*`

## build.py

Calls `tagy.generate()` — a local utility for tag generation (not part of the standard Hugo workflow).
