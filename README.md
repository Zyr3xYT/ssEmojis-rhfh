# ssEmojis

**Shark Studios | zyr3xyt.yml**
**Discord - https://discord.gg/yzTTAeNArf**

Universal Minecraft emoji & sprite shortcode plugin for Paper.

## Identity

| Property | Value |
|----------|-------|
| Plugin name | `ssEmojis` |
| Developer | `zyr3xyt.yml` |
| Main package | `zyr3xyt.yml.ssemojis` |
| Main class | `ssEmojis` |
| API class | `ssEmoji` |
| Command | `/ssem` (aliases `/emoji`, `/emojis`) |
| Permission prefix | `ssem` |

## Features

- Shortcode syntax `:diamond:`, `:minecraft:netherite_sword:`, `:custom:server_logo:`
- Native Adventure sprite components for vanilla items (no resource pack required for built-in Minecraft sprites on modern clients)
- Glyph-based custom sprites (require a resource pack)
- MiniMessage integration (`<sprite:diamond>`)
- Immutable, thread-safe sprite registry with atomic reload
- Optional PlaceholderAPI expansion
- Public API for other plugins
- Resource-pack delivery on join when configured

## Requirements

- **Server**: Paper (or compatible) 1.21+
- **Java**: 21
- **Clients**: Modern clients that support Adventure ObjectContents / sprite components (roughly 1.20.5+)

See `COMPATIBILITY.md` for honest version notes.

## Installation

1. Drop `ssEmojis.jar` into the server `plugins/` folder.
2. Start the server once to generate `config.yml`.
3. Edit sprites / resource-pack settings as needed.
4. `/ssem reload`

## Usage

```text
Welcome :diamond:
Kit: :netherite_sword: :diamond_pickaxe:
Reward: :golden_apple:
```

Namespaced:

```text
:minecraft:apple:
:custom:server_logo:
```

MiniMessage:

```text
<red>Hello <sprite:diamond></red>
<gradient:#00B8FF:#FF0000>Shark Studios <sprite:custom:server_logo></gradient>
```

## Commands

| Command | Permission | Description |
|---------|------------|-------------|
| `/ssem help` | — | Help |
| `/ssem reload` | `ssem.reload` | Reload config |
| `/ssem list` | `ssem.list` | List sprites |
| `/ssem info <id>` | `ssem.list` | Sprite details |
| `/ssem test <id>` | `ssem.test` | Preview |
| `/ssem pack` | `ssem.pack` | Resource-pack status |
| `/ssem image ...` | `ssem.image` | Custom image management |

## Public API

```java
ssEmoji api = ssEmoji.getInstance();
Component msg = api.parse("Hello :diamond:");
api.registerSprite("custom:logo", "\uE200");
boolean exists = api.hasSprite("diamond");
```

## Custom images / glyphs

Custom PNGs can be registered via the API or config. Clients still need a resource pack that maps the assigned private-use glyph to the image. True resource-pack-free arbitrary PNG rendering in chat or scoreboards is **not** supported by vanilla Minecraft and is not claimed by this plugin.

## Building

```shell
cd ssEmojis
gradle build
```

Output: `build/libs/ssEmojis.jar`

## License & attribution

Original architecture inspired by AstraEmojis (Astra Studio). Rebranded and extended under the ssEmojis / Shark Studios identity as specified.
