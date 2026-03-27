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

## 📝 Placeholder Documentation

### 🔹 Message Placeholders (messages.yml)

These placeholders are used in `messages.yml` and are automatically replaced by the plugin:

#### **Punishment Information**
| Placeholder | Description | Example |
|------------|-------------|----------|
| `<id>` | Punishment ID number | `#1234` |
| `<player>` | Target player's name | `Notch` |
| `<uuid>` | Player's UUID | `069a79f4-44e9-4726-a5be-fca90e38aaf5` |
| `<reason>` | Punishment reason | `Cheating` |
| `<staff>` | Staff member who issued punishment | `Admin` |
| `<type>` | Punishment type | `BAN`, `MUTE`, `WARN`, `KICK` |
| `<duration>` | Time remaining or duration | `7 days, 3 hours`, `Permanent` |
| `<date>` | Date punishment was issued | `15.03.2026 14:30:00` |
| `<status>` | Punishment status | `Active`, `Inactive`, `Expired` |

#### **Player Information**
| Placeholder | Description | Example |
|------------|-------------|----------|
| `<last_seen>` | Last time player was online | `15.03.2026 14:30:00` |
| `<last_ip>` | Player's last known IP address | `127.0.0.1` or `[Hidden]` |
| `<account_name>` | Alt account name (for ban evasion) | `Notch_Alt` |
| `<banned_account>` | Original banned account | `Notch` |

#### **System & Navigation**
| Placeholder | Description | Example |
|------------|-------------|----------|
| `<server_name>` | Server name from config | `My Minecraft Server` |
| `<discord_invite>` | Discord invite link from config | `discord.gg/example` |
| `<page>` | Current GUI page number | `1` |
| `<max_pages>` | Total pages in GUI | `5` |
| `<usage>` | Command usage syntax | `/ban <player> <reason>` |
| `<preset>` | Preset name | `CHEATING` |
| `<message>` | Generic message content | varies |

#### **Status & Metadata**
| Placeholder | Description | Example |
|------------|-------------|----------|
| `<version>` | Plugin version | `1.2.4` |
| `<author>` | Plugin author | `kotori` |
| `<current_version>` | Current installed version | `1.2.3` |
| `<latest_version>` | Latest available version | `1.2.4` |
| `<db_status>` | Database connection status | `Connected` |
| `<db_ping>` | Database ping in ms | `5` |
| `<net_status>` | Network sync status | `Enabled` |
| `<command>` | Command name | `/ban` |
| `<description>` | Command description | `Bans a player` |

#### **GUI Specific**
| Placeholder | Description | Example |
|------------|-------------|----------|
| `<note_text>` | Note content | `Player warned for spam` |

---

### 🔹 PlaceholderAPI Integration

**Requires:** [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/)

Use these placeholders in **any** plugin that supports PlaceholderAPI (scoreboard, tab list, chat plugins, etc.):

#### **Status Checks**
| Placeholder | Description | Returns |
|------------|-------------|----------|
| `%justbans_is_banned%` | Check if player is currently banned | `Yes` or `No` |
| `%justbans_is_muted%` | Check if player is currently muted | `Yes` or `No` |
| `%justbans_active_bans%` | Total number of active bans on server | `42` |

#### **Ban Information**
| Placeholder | Description | Returns |
|------------|-------------|----------|
| `%justbans_ban_id%` | Active ban punishment ID | `1234` or `N/A` |
| `%justbans_ban_reason%` | Reason for active ban | `Hacking` or `N/A` |
| `%justbans_ban_staff%` | Staff who issued the ban | `Admin` or `N/A` |
| `%justbans_ban_date%` | Date when banned | `15.03.2026 14:30:00` or `N/A` |
| `%justbans_ban_expiry%` | Ban expiration date | `22.03.2026 14:30:00`, `Permanent`, or `N/A` |
| `%justbans_ban_expire_date%` | Alias for ban_expiry | Same as above |
| `%justbans_ban_duration%` | Time remaining on ban | `7 days, 3 hours`, `Permanent`, or `N/A` |

#### **Mute Information**
| Placeholder | Description | Returns |
|------------|-------------|----------|
| `%justbans_mute_id%` | Active mute punishment ID | `1235` or `N/A` |
| `%justbans_mute_reason%` | Reason for active mute | `Spamming` or `N/A` |
| `%justbans_mute_staff%` | Staff who issued the mute | `Moderator` or `N/A` |
| `%justbans_mute_date%` | Date when muted | `15.03.2026 14:30:00` or `N/A` |
| `%justbans_mute_expiry%` | Mute expiration date | `15.03.2026 16:30:00`, `Permanent`, or `N/A` |
| `%justbans_mute_expire_date%` | Alias for mute_expiry | Same as above |
| `%justbans_mute_duration%` | Time remaining on mute | `2 hours, 15 minutes`, `Permanent`, or `N/A` |

**Example Usage:**
```yaml
# In DeluxeMenus - Ban Info GUI
ban_info:
  material: BARRIER
  display_name: "&cBan Information"
  lore:
    - "&7Banned: %justbans_is_banned%"
    - "&7Ban ID: &c#%justbans_ban_id%"
    - "&7Reason: &f%justbans_ban_reason%"
    - "&7Banned by: &e%justbans_ban_staff%"
    - "&7Banned on: &f%justbans_ban_date%"
    - "&7Expires: &f%justbans_ban_expiry%"
    - "&7Time remaining: &a%justbans_ban_duration%"

# In TAB plugin - Scoreboard
scoreboard:
  lines:
    - "&cBanned: %justbans_is_banned%"
    - "&6Muted: %justbans_is_muted%"
    - "&7Active Bans: %justbans_active_bans%"
```

---

### 🔹 Discord Webhook Placeholders

**Location:** `webhooks.yml` templates

These placeholders use `{curly_braces}` instead of `<angle_brackets>`:

| Placeholder | Description | Example |
|------------|-------------|----------|
| `{id}` | Punishment ID | `1234` |
| `{player}` | Target player name | `Notch` |
| `{staff}` | Staff member name | `Admin` |
| `{reason}` | Punishment reason | `Hacking` |
| `{duration}` | Punishment duration | `7 days`, `Permanent` |
| `{type}` | Punishment type | `BAN`, `MUTE` |
| `{server}` | Server ID from config | `survival` |

**Example:**
```yaml
templates:
  punish:
    title: "[{server}] New {type}"
    footer: "Punishment ID: #{id}"
```

---

### 🎨 MiniMessage Format Support

All message placeholders support [MiniMessage](https://docs.advntr.dev/minimessage/format.html) formatting:

```yaml
# Gradients
ban_screen:
  - "<gradient:#FF0000:#00FF00>You are banned!</gradient>"

# Hover text
mute_message: "<hover:show_text:'Muted by <staff>'>You are muted</hover>"

# Click actions
help_text: "<click:open_url:'https://example.com'>Click for appeal</click>"

# Colors
broadcast_ban: "<red><player></red> was banned by <green><staff></green>"
```

---

<p align="center">Made with ❤️ by <strong>kotori</strong></p>
