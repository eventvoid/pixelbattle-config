# Pixel Battle Config

Runtime configuration for Pixel Battle seasons.

The server reads `test/season.json` through `PIXELBATTLE_SEASON_CONFIG_URL` and periodically refreshes it without restart.

## `season.json`

```json
{
  "active": true,
  "starts_at": "2026-05-11T00:00:00+05:00",
  "ends_at": "2026-05-13T00:00:00+05:00",
  "cooldown_seconds": 0.5,
  "width": 1000,
  "height": 1000,
  "palette": [
    "#FFFFFF",
    "#000000"
  ]
}
```

## Fields

- `active` - enables or disables pixel placement. If `false`, users can view the board and archives, but cannot place pixels.
- `starts_at` - season start time in RFC3339 format.
- `ends_at` - season end time in RFC3339 format.
- `cooldown_seconds` - placement cooldown in seconds. Decimals are supported, for example `2.5`.
- `width` - board width in pixels.
- `height` - board height in pixels.
- `palette` - available season colors as `#RRGGBB`.

## Rules

- Only one season can be active.
- `ends_at` must be later than `starts_at`.
- `palette` can contain at most 128 colors.
- `width`, `height`, and `palette` should be changed only between seasons after the current season is archived and cleared, because current map data and pixel history depend on coordinates and color ids.
- If the file is unavailable or invalid, the server keeps the previous valid config. On initial startup it uses environment fallback values.
