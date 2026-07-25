# evenmoreutils

[moreutils](https://joeyh.name/code/moreutils/) is a collection of the Unix tools
that should've shipped by default. This is the personal sequel: a growing pile of
Rust CLI tools for finding, fetching, and reading things — built for one specific
habit.

The pattern behind most of these: cast a query out at a pile of open, public, or
self-hostable servers (SearXNG instances, Redlib proxies, Torznab indexers, Shodan,
OSM, Wikimedia, Codeberg/Forgejo, whatever's listening), merge and dedupe what comes
back, and print it in a terminal-native format that's actually comfortable to live
in. No browser tabs, no API keys where they can be avoided, no scraping when a real
API exists.

Every tool below is its own repo, vendored here as a git submodule under `tools/`.

## Getting the tools

```sh
git clone --recurse-submodules https://github.com/kernelzeroday/evenmoreutils.git
cd evenmoreutils

# or, if you already cloned without --recurse-submodules:
git submodule update --init --recursive
```

Each tool is a standalone Rust crate. Build and install any one of them with:

```sh
cd tools/<name>
cargo install --path .
```

To update every submodule to its upstream `main`/`master`:

```sh
git submodule update --remote --merge
```

## The tools

### Search & discovery

Fan out to the open web instead of one walled garden.

| Tool | Binary | What it does |
|---|---|---|
| [searx](tools/searx) | `searx` | Multi-provider SearXNG CLI — fans out to multiple SearXNG instances, merges & dedupes results, with SQLite-backed instance health tracking and response caching |
| [reddit-rs](tools/reddit-rs) | `reddit` | Browse Reddit via Redlib proxies from the terminal — no Reddit API key, no login |
| [shodan-rs](tools/shodan-rs) | `shodan` | Shodan CLI, rewritten in Rust |
| [osm](tools/osm) | `osm` | Search and read OpenStreetMap data from the terminal |
| [wiki](tools/wiki) | `wiki` | Search and read Wikipedia and sister sites (Wikiquote, Wikinews, Wiktionary) in any language, from the terminal |
| [hf-cli](tools/hf-cli) | `hf-cli` | Search and browse the Hugging Face model hub from the terminal |
| [ollama-models](tools/ollama-models) | `ollama-models` | Search and browse the Ollama model registry — no browser required |
| [hn-cli](tools/hn-cli) | `hn` | Hacker News CLI — top, new, and best stories |
| [groundnews-rs](tools/groundnews-rs) | `groundnews` | Ground News CLI — news bias, blindspots, and source coverage from the terminal |
| [metacritic](tools/metacritic) | `metacritic` | Query Metacritic from the terminal — no API keys, no scraping |
| [polymarket-cli](tools/polymarket-cli) | `polymarket` | Query prediction markets — search, view a market, chart its price history |
| [internet-research](tools/internet-research) | `dialup` | Curated catalog + connector for public-access Unix systems, tilde clubs, BBSes, and MUDs discovered via Shodan |

### Torrents & acquisition

Talk directly to indexers over their real protocols (Torznab, site search) instead
of scraping a web UI.

| Tool | Binary | What it does |
|---|---|---|
| [magnets-cli](tools/magnets-cli) | `magnets` | Async Torznab client — query self-hosted Bitmagnet, Jackett, or any Torznab-compatible indexer for magnet links |
| [tpb-cli](tools/tpb-cli) | `tpb` | Search Torznab-compatible torrent indexers from the terminal |
| [nyaa-cli](tools/nyaa-cli) | `nyaa` | Search Nyaa.si for anime torrents, print magnet links straight to stdout |
| [rutracker](tools/rutracker) | `rutracker` | Search RuTracker and fetch magnet links |
| [torrentget](tools/torrentget) | `torrentget` | Search and fetch torrent download links from TorrentDownload |
| [audiobookbay-cli](tools/audiobookbay-cli) | `audiobookbay` | Search AudioBookBay for audiobook torrents |
| [ytsmx](tools/ytsmx) | `yts` | Browse the YTS movie catalog from the terminal |

### Streaming & casting

| Tool | Binary | What it does |
|---|---|---|
| [youtube-cli](tools/youtube-cli) | `youtube` | YouTube from the terminal — search, trending, video details |
| [tubecast](tools/tubecast) | `tubecast` | Generic YouTube caster over the Lounge API — cast to Playlet, native YouTube TV apps, and more |
| [jellyfin-cli](tools/jellyfin-cli) | `jf` | Jellyfin media server CLI — Quick Connect login, browse, control playback |
| [roku-cli](tools/roku-cli) | `roku` | Control a Roku device directly over ECP on your LAN — keypresses, text input, app launch |

### Reading

| Tool | Binary | What it does |
|---|---|---|
| [epub](tools/epub) | `epub` | Non-interactive EPUB text extraction — list chapters, extract by index/range, pipe to stdout |

### AI / LLM tooling

| Tool | Binary | What it does |
|---|---|---|
| [anonkeyst](tools/anonkeyst) | `anonkeyst` | CLI for anonkey.st, an anonymous OpenAI-compatible proxy |
| [cla](tools/cla) | `cla` | Claude Code profile launcher — multi-provider (Anthropic, DeepSeek, OpenRouter) usage tracking, token caching, config aliases, shell completions |

### Federated / self-hosted infra

| Tool | Binary | What it does |
|---|---|---|
| [cb](tools/cb) | `cb` | A Forgejo CLI — works with Codeberg and any Forgejo instance |
| [netnews-rs](tools/netnews-rs) | `netnews` | Command-line interface for NetNewsWire |

### Just for fun

| Tool | Binary | What it does |
|---|---|---|
| [subversive](tools/subversive) | `subversive` | 1,360+ embedded quotes from powerful and subversive figures, across 23 categories |
| [pcnoise](tools/pcnoise) | `pcnoise` | Retrofuture computer noise synthesizer — beeps, whistles, and digital artifacts from a 90s cyberdeck. 36 procedural sounds, scenes, generative mode, spectral analysis |
| [say-rs](tools/say-rs) | `say` | Rust reimplementation of macOS `say`, with word highlighting and progress |
| [magic-greyscale](tools/magic-greyscale) | `magic_greyscale` | MTG & Pokémon greyscale proxy sheet generator, for printing cards on a B&W laser printer |
| [d2info-rs](tools/d2info-rs) | `d2info` | Diablo II toolkit — build planner, save file editor/reader, and item database fetcher |

## Why submodules

Each tool ships, versions, and releases independently — they're real crates with
their own history, issues, and `cargo install --path .` workflow. Submodules keep
that independence while still giving this repo one place to discover the whole set
and pin a known-good combination of versions.

## License

Each submodule carries its own license — check the individual tool's repo. This
metarepo (the README and submodule wiring) is public domain / CC0; do whatever
you want with it.
