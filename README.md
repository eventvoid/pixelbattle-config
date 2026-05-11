# pixelbattle-config

Runtime configuration repository for Pixel Battle seasons.

The server periodically reads a selected `season.json` file from this repository and updates season state without restart.

## Structure

- `prod/season.json` - production season config
- `test/season.json` - test season config

## season.json

```json
{
  "active": true,
  "starts_at": "2026-04-27T00:00:00+05:00",
  "ends_at": "2026-05-03T23:59:00+05:00",
  "cooldown_seconds": 30
}
