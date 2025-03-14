# Godot Workflows

A collection of GitHub Actions workflows for Godot Engine game development that handle building and deploying Godot games.

## Available Workflows

### Build Game (`build-game.yaml`)

Builds your Godot game for specified platforms.

**Inputs:**

| Input | Type | Required? | Default | Description |
|-------|------|----------|---------|-------------|
| `runner` | string | No | `ubuntu-latest` | The linux runner to when building the game |
| `godot-version` | string | No | `4.4` | Godot version to use. Should be of the form `3.x` or `4.x`. |
| `web-preset` | string | No | | The export preset to use for web exports. |
| `web-export-name` | string | No | `index.html` | The name of the exported file for web exports. |
| `web-artifact-name` | string | No | `web-export` | The name to use when uploading web build artifact |
| `windows-preset` | string | No | | The export preset to use for windows exports. |
| `windows-export-name` | string | No | `game.exe` | The name of the exported file for windows exports. |
| `windows-artifact-name` | string | No | `windows-export` | The name to use when uploading Windows build artifact |
| `inject-godot-config` | boolean | No | `false` | Whether to inject the branch and commit into the project.godot file |

At least one of `web-preset` or `windows-preset` must be provided.

**Outputs:**

| Output | Description |
|--------|-------------|
| `web-artifact-name` | The name of the artifact containing the web build or an `''` if no artifact was uploaded |
| `windows-artifact-name` | The name of the artifact containing the Windows build or an `''` if no artifact was uploaded |


### Deploy to Itch.io (`deploy-itch.yaml`)

Deploys your game to itch.io.

**Inputs:**

| Input | Type | Required? | Default | Description |
|-------|------|----------|---------|-------------|
| `runner` | string | No | `ubuntu-latest` | The linux runner to when deploying to itch.io |
| `itch-user` | string | Yes | | The itch.io username of the owner of the game |
| `itch-game` | string | Yes | | The name of the itch.io game (as entered in the Project URL) |
| `game-version` | string | No | | The version of the game to deploy (can be a version number or a file path) |
| `web-channel` | string | No | `web` | The itch.io upload channel to use for web exports |
| `web-artifact-name` | string | No | | Name of the web build artifact |
| `windows-channel` | string | No | `windows` | The itch.io upload channel to use for Windows exports |
| `windows-artifact-name` | string | No | | Name of the Windows build artifact |

**Secrets:**
| Secret | Required? | Description |
|--------|-----------|-------------|
| `butler-api-key` | Yes | The API key for butler. Walkthrough for attaining this [here](https://itch.io/docs/butler/login.html#running-butler-from-ci-builds-travis-ci-gitlab-ci-etc). |
