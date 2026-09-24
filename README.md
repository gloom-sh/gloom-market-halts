# Market Halts for Gloom

Every current and recent US trading halt from the Nasdaq Trader feed, with the halt reason code, halt time, and resumption times.

## Install

Requires Gloom 0.15.0 or newer. Gloom restores this plugin once for existing installations when it moves out of the core app: saved panes keep working because the pane and template ids are unchanged, a previously disabled plugin stays disabled, and a deliberate removal is respected.

```sh
gloomberb install gloom-sh/gloom-market-halts
```

Open `HALT` in the command bar. Also in the hosted web app at term.gloom.sh, where the host proxies the data source.

## Usage

All, Active and Resumed filter the table from the pane's tab strip; `f` cycles them. `[` and `]` cycle the sort, `r` refreshes. Activate a row to open the ticker. The pane refreshes on its own and reports the feed's status in the footer and the Connections pane.

A narrow pane drops columns instead of scrolling sideways, in this order: market, quote resumption, reason code, company. The status column always stays.

## Data

The public Nasdaq Trader halts RSS feed at `nasdaqtrader.com`. Fetched directly; nothing goes through Gloom Cloud.

## Development

```sh
bun install
# Link a Gloom checkout, as the plugin installer does:
ln -s /path/to/gloomberb node_modules/gloomberb
ln -s /path/to/gloomberb/node_modules/react node_modules/react
bun run typecheck
bun test
```

`gloomberb` and `react` are peer dependencies, never real ones. Gloom symlinks its own copies into every plugin directory on install and on load, so there is exactly one instance of each in the process. CI links the host the same way.

## License

MIT
