# Godot Workflows

A collection of GitHub Actions workflows for Godot Engine game development that handle building and deploying Godot games.

## Available Workflows

### Build Game (`build-game.yaml`)

Builds your Godot game for specified platforms.

**Inputs:**

| Input | Type | Required? | Default | Description |
|-------|------|----------|---------|-------------|
| `runner` | string | No | `ubuntu-latest` | The GitHub runner to use |
| `godot-version` | string | No | `4.4` | Godot version to use. Should be of the form `3.x` or `4.x`. |
| `web-preset` | string | No | | Export preset name for web builds |
| `web-export-name` | string | No | `index.html` | Filename for web export |
| `web-artifact-name` | string | No | `web-export` | Artifact name for web builds |
| `windows-preset` | string | No | | Export preset name for Windows builds |
| `windows-export-name` | string | No | `game.exe` | Filename for Windows export |
| `windows-artifact-name` | string | No | `windows-export` | Artifact name for Windows builds |

At least one of `web-preset` or `windows-preset` must be provided.

**Outputs:**

| Output | Description |
|--------|-------------|
| `web-artifact-name` | Name of the web build artifact |
| `windows-artifact-name` | Name of the Windows build artifact |


### Deploy to Itch.io (`deploy-itch.yaml`)

Deploys your game to itch.io.

**Inputs:**

| Input | Type | Required? | Default | Description |
|-------|------|----------|---------|-------------|
| `runner` | string | No | `ubuntu-latest` | GitHub runner to use |
| `itch-user` | string | Yes | | Your itch.io username |
| `itch-game` | string | Yes | | Your itch.io game identifier |
| `game-version` | string | No | | Version to deploy (can be a version string or file path) |
| `web-channel` | string | No | `web` | Itch.io channel for web builds |
| `web-artifact-name` | string | No | | Name of the web build artifact |
| `windows-channel` | string | No | `windows` | Itch.io channel for Windows builds |
| `windows-artifact-name` | string | No | | Name of the Windows build artifact |

**Secrets:**
| Secret | Required? | Description |
|--------|-----------|-------------|
| `butler-api-key` | Yes | Your itch.io Butler API key. Walkthrough for attaining this [here](https://itch.io/docs/butler/login.html#running-butler-from-ci-builds-travis-ci-gitlab-ci-etc). |
