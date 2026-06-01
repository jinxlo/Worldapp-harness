# WorldApp Harness

WorldApp Harness is an AI coding agent for the terminal, configured for the World App Technologies API by default.

## Default AI Provider

WorldApp uses the World App Technologies OpenAI-compatible API.

- Base URL: `https://platform.worldapptechnologies.com/api/v1`
- Main model: `world-app-technologies-api/nulu-4.8`
- Fast model: `world-app-technologies-api/nulu-4.8-flash`

Users only need a World App Technologies API key.

```bash
export WORLDAPP_API_KEY="sk_wat_your_key"
```

## Install From Source

```bash
git clone https://github.com/jinxlo/Worldapp-harness.git
cd Worldapp-harness
bun install --ignore-scripts
cd packages/opencode
bun run build --single --skip-install
./dist/worldapp-linux-x64/bin/worldapp --help
```

## Run

```bash
worldapp
```

Or run a one-shot prompt:

```bash
worldapp run "Review this project"
```

## Configuration

Project configuration is loaded from `worldapp.json`, `worldapp.jsonc`, and `.worldapp/` directories.

Example provider override:

```json
{
  "provider": {
    "world-app-technologies-api": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "World App Technologies API",
      "options": {
        "baseURL": "https://platform.worldapptechnologies.com/api/v1",
        "apiKey": "{env:WORLDAPP_API_KEY}"
      },
      "models": {
        "nulu-4.8": {},
        "nulu-4.8-flash": {}
      }
    }
  },
  "model": "world-app-technologies-api/nulu-4.8",
  "small_model": "world-app-technologies-api/nulu-4.8-flash",
  "enabled_providers": ["world-app-technologies-api"]
}
```

## Development

```bash
cd packages/opencode
bun typecheck
bun run build --single --skip-install
```

## License

This project is distributed under the MIT License. See `LICENSE` for the required upstream copyright notice.
