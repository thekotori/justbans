# ⚖️ justBans

A modern, high-performance, and network-ready punishment system, built for reliability and ease of use on any **Paper**, **Folia**, or **Spigot-based** server.

<p align="center">
  <img src="https://img.shields.io/badge/Author-kotori-lightgrey?style=for-the-badge" alt="Author" />
  <img src="https://img.shields.io/badge/API-1.21+-brightgreen?style=for-the-badge" alt="API Version" />
  <img src="https://img.shields.io/badge/Platform-Paper_|_Folia-blue?style=for-the-badge" alt="Platform" />
</p>

---

## ✨ Features

- ⚖️ **Full Punishment Suite** — Manage bans, mutes, warnings, and kicks with precision.
- 🌐 **Network Support** — Instantly sync punishments across BungeeCord and Velocity proxies.
- 🖥️ **GUI Interface** — View player histories, ban lists, and detailed info visually.
- 🛡️ **Ban Evasion Detection** — Automatically catch and punish alt accounts.
- 🚀 **High Performance** — Asynchronous, non-blocking core ensures zero lag.
- ⚙️ **Punishment Presets** — Create templates for fast, consistent moderation.
- 📝 **Player Notes** — Add persistent staff notes to player records.
- ιε **Folia Compatible** — Modern scheduler support for thread-safe execution.
- 💾 **Flexible Storage** — Supports H2 (single server) or MySQL (network-wide).
- 🎨 **Highly Customizable** — Edit messages, formats, behavior, and more.
- 💎 **MiniMessage Support** — Stylish messages with gradients, hovers, and clicks.
- 🧩 **PlaceholderAPI Support** — Display punishment status anywhere.
- ιε **Staff Hierarchy** — Power levels prevent lower staff from punishing higher ranks.
- 🔔 **Discord Webhooks** — Send real-time punishment logs to Discord.
- ✏️ **Punishment Editing** — Modify reasons and durations of active punishments.

---

## 📦 Installation

1. Download the latest `justBans.jar`.
2. Stop your Minecraft server.
3. Place the file in your `/plugins/` directory.
4. *(Optional)* Install **ProtocolLib** for advanced mute handling.
5. *(Optional)* Install **PlaceholderAPI** for placeholder support.
6. Start the server to generate configuration files.
7. Enter your **license key** in `config.yml`.
8. Customize `config.yml`, `messages.yml`, `presets.yml`, etc.
9. Reload with `/justbans reload`.

---

## ⚙️ Configuration

### `config.yml`

```yaml
license-key: "ENTER_YOUR_LICENSE_KEY_HERE"

settings:
  timezone: "UTC"
  date-format: "dd.MM.yyyy HH:mm:ss"
  console_name: "Console"

database:
  type: H2 # or MYSQL
  mysql:
    host: "localhost"
    port: 3306
    # more options...

sync:
  enabled: true # Enable for Bungee/Velocity support

alts:
  check_on_join: true
  ban_evasion_action: BAN
  ban_evasion_reason: "Ban Evasion"
```

---

### `messages.yml` (MiniMessage supported)

```yaml
prefix: "<gray>[<gradient:#00AEEF:#3645A5>justBans</gradient>]<gray>"

no_permission: "<prefix> <icon_error> You do not have permission to do that."
player_not_found: "<prefix> <icon_error> Player <#00AEEF><player></#00AEEF> not found."

broadcast_ban: "<prefix> <gray>[#<id>] <#00AEEF><player></#00AEEF><white> was banned by <#00AEEF><staff></#00AEEF><white> for '<reason><white>'. <gray>(<duration>)"

ban_screen:
  - ""
  - "<gradient:#00AEEF:#3645A5>You have been banned from <server_name></gradient>"
  - "<gray>Reason: <white><reason>"
  - "<gray>Expires: <white><duration>"
```

---

### `presets.yml`

```yaml
presets:
  CHEATING:
    type: BAN
    duration: "30d"
    reason: "Cheating / Unfair Advantages"
    permission: "justbans.preset.cheating"
  SPAMMING:
    type: MUTE
    duration: "2h"
    reason: "Spamming in chat"
    permission: "justbans.preset.spamming"
```

---

## ⌨️ Commands & Permissions

### 🔧 Commands

| Command                                           | Description                                         |
|--------------------------------------------------|-----------------------------------------------------|
| `/ban <player> <reason/preset> [duration]`       | Bans a player                                       |
| `/ipban <player> <reason/preset> [duration]`     | IP-bans a player and their alts                     |
| `/mute <player> <reason/preset> [duration]`      | Mutes a player                                      |
| `/ipmute <player> <reason/preset> [duration]`    | IP-mutes a player and their alts                    |
| `/warn <player> <reason/preset>`                 | Issues a warning to a player                        |
| `/kick <player> [reason]`                        | Kicks a player from the server                      |
| `/unban <player>`                                | Unbans a player                                     |
| `/unmute <player>`                               | Unmutes a player                                    |
| `/unwarn <player>`                               | Removes the latest warning from a player           |
| `/check <player>`                                | Opens a GUI showing the player's punishment history |
| `/checkid <id>`                                  | Shows detailed info for a specific punishment ID    |
| `/banlist`                                       | Opens a GUI showing all active bans                |
| `/note <player> <add/delete> [text/id]`          | Adds or deletes a note for the player              |
| `/editban <id> <reason/duration> <value>`        | Edits the reason or duration of a ban              |
| `/justbans <reload/help>`                        | Reloads config files or shows the help menu        |


> **Tip**: Add `-s` or `--silent` to any punishment command to suppress the public broadcast.

---

### 🔐 Permissions

| Permission | Description | Default |
|------------|-------------|---------|
| `justbans.*` | Full access | `op` |
| `justbans.command.*` | All commands | `op` |
| `justbans.notify.*` | All notifications | `op` |
| `justbans.bypass.*` | Full immunity | `op` |
| `justbans.command.admin` | `/justbans` base command | `op` |
| `justbans.command.ban` | `/ban` | `op` |
| `justbans.command.ipban` | `/ipban` | `op` |
| `justbans.command.mute` | `/mute` | `op` |
| `justbans.command.ipmute` | `/ipmute` | `op` |
| `justbans.command.warn` | `/warn` | `op` |
| `justbans.command.kick` | `/kick` | `op` |
| `justbans.command.unban` | `/unban` | `op` |
| `justbans.command.unmute` | `/unmute` | `op` |
| `justbans.command.unwarn` | `/unwarn` | `op` |
| `justbans.command.check` | `/check`, `/checkid` | `op` |
| `justbans.command.banlist` | `/banlist` | `op` |
| `justbans.command.note` | `/note` | `op` |
| `justbans.command.note.add` | Add notes | `op` |
| `justbans.command.note.delete` | Delete notes | `op` |
| `justbans.command.edit` | `/editban` | `op` |
| `justbans.notify.broadcast` | See public broadcasts | `op` |
| `justbans.notify.silent` | See silent punishments | `op` |
| `justbans.notify.evasion` | See alt evasion alerts | `op` |
| `justbans.bypass.ban` | Prevent bans | `op` |
| `justbans.bypass.mute` | Prevent mutes | `op` |

---

## 🧩 PlaceholderAPI

| Placeholder | Description |
|------------|-------------|
| `%justbans_is_banned%` | Returns `Yes` or `No` |
| `%justbans_is_muted%` | Returns `Yes` or `No` |
| `%justbans_active_bans%` | Total number of active bans |

---

<p align="center">Made with ❤️ by <strong>kotori</strong></p>
