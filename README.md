# 🏆 Cores Minigame 
[![Minecraft Version](https://img.shields.io/badge/Minecraft-latest-brightgreen.svg)](https://www.spigotmc.org/)
[![Platform](https://img.shields.io/badge/Platform-PaperMC%20%7C%20Spigot%20%7C%20Bukkit%20%7C%20Purpur-blue.svg)](https://papermc.io/)
[![Dependencies](https://img.shields.io/badge/Dependencies-PlaceholderAPI-orange.svg)]()

An ultra-configurable, high-performance **Cores** minigame plugin. Bring the classic, fast-paced tactical PvP experience to your network or community server with modular arena setups, automated rollbacks, and full PlaceholderAPI support!

---

## 🎮Game Mechanics
Players are split into two teams: **Team Red** and **Team Blue**.
* **The Cores:** Each team has 2 cores (beacon blocks). The primary objective is to mine the opposing team's cores!
* **Defense & Alarm:** Whenever an opponent approaches a core (within a 4-5 block radius), an unmistakable audible alarm sounds for the defending team.
* **Respawns & Loot:** Players can respawn indefinitely; however, upon death, they lose their temporary equipment and immediately receive their configurable default kit. Valuable iron and diamond blocks are scattered across the map for upgrades.
* **Victory Conditions:** The game ends immediately if both of a team's cores are destroyed or the time limit expires. The team that still possesses at least one core wins.
---

## ✨ Features

* 🛠️ **100% Configurable:** Every message, sound, item layout, and GUI element can be customized in the config files.
* 🏟️ **Multi-Arena System:** Create an unlimited number of arenas using simple in-game admin commands.
* 🔄 **Automatic Map Reset:** After every game, the arena is completely restored to its original state (block rollback, chest refill).
* 🛡️ **Spawn Protection:** A configurable protection radius (default: 15 blocks) around team spawns prevents the map from being mined in this area.
* 📦 **Modern GUIs (Spectator & Join System):**
  * Quickly join the most active arena.
  * Dynamic arena overview: Displays name, status (`Waiting`, `Playing`, `Ending`), and player count. Ongoing games are automatically moved to the end of the list and marked as accessible to spectators.
* 📊 **Integrated Statistics (Stats):** Tracks `Games Played`, `Wins`, and `Losses` per player.
* 📢 **Isolated Chat & Tab List:** Each arena has its own chat and tab list. Spectators have a separate, private chat. Teams are color-coded throughout!
* 🚀 **PlaceholderAPI Support:** Uses external placeholders in all configurations and provides custom placeholders for player stats and arena states.
* 💎 **Cosmetic Particles:** Exclusive particle effects for players with special permissions.
* 💰 **Reward System:** Execute custom console commands at the end of the game (e.g., awarding coins via your economy system for wins and kills).
* 👑 **Rank support:** Display the prefix or suffix of your players' ranks in every plugin message using PlaceholderAPI.

---

## 📋 Commands & Permissions

All commands run through the main `/cores` command.

### 👥 Player commands
* `/cores join` - Opens the join gui.
* `/cores leave` - Leaves the game.
* `/cores stats` - Shows the player stats in chat.

### ⚡ VIP / Premium commands
* `/cores start` - Shortens the countdown in the waiting lobby to 5 seconds. (`cores.command.start`).
* `/cores forcestart` - Start the game immediately in the waiting lobby. (`cores.command.forcestart`).

### 🛠️ Admin commands (`cores.admin`)
* `/cores setlobby` - Sets the main lobby for the game.
* `/cores createarena <name>` - Creates an arena.
* `/cores deletearena <name>` - Deletes an arena.
* `/cores setwaiting <arena>` - Sets the spawn on the waiting lobby.
* `/cores setspectator <arena>` - Sets the spectator spawn.
* `/cores setspawn <arena> <red/blue>` - Sets the team spawnpoint.
* `/cores setcore <arena> <red/blue> <1/2>` - Sets a beacon at the position standing on.
* `/cores setmaxplayers <arena> <maxProTeam>` - Defines maximum players per team.
* `/cores setminplayers <arena> <minProTeam>` - Defines minimum players per team to start game.
* `/cores setmaxtime <arena> <seconds>` - Sets max playtime.
* `/cores enable <arena>` - Enables arena.
* `/cores disable <arena>` - Disables arena.
* `/cores info <arena>` - Shows info about given arena in chat.
* `/cores reload` - Reloads the plugin.

---

## 🧩 Placeholders (PlaceholderAPI)

* `%cores_stats_games_played%` - Number of played games.
* `%cores_stats_wins%` - Number of won games.
* `%cores_stats_losses%` - Number of lost games.
* `%cores_in_arena%` - Is player in arena (true | false).
* `%cores_arena_name%` - Name of arena.
* `%cores_arena_state%` - State of arena.
* `%cores_arena_players%` - Current players in arena.
* `%cores_arena_max_players%` - Max players of arena.
* `%cores_arena_time_left%` - Playtime left in arena.
* `%cores_arena_red_players%` - Count of players in red team.
* `%cores_arena_blue_players%` - Count of players in blue team.
* `%cores_player_kills%` - Kill count.
* `%cores_player_cores_destroyed%` - Cores destroyed count.
* `%cores_player_team%` - Name if team.
* `%cores_player_team_color%` - Color of team.
* `%cores_player_spectator%` - Is spectator (true | false).
* `%cores_arena_<arena>_state%` - Status of specified arena.
* `%cores_arena_<arena>_players%` - Playercount of specified arena.
* `%cores_arena_<arena>_max_players%` - Max players of specified arena.
* `%cores_arena_<arena>_name%` - Clean name of specified arena.

## 📃Config
```
# Cores Plugin - Main Configuration
# You can use PlaceholderAPI placeholders in most messages.

# General settings
lobby-location: null  # Set via /cores setlobby

prefix-placeholder: "%luckperms_prefix%"
suffix-placeholder: "%luckperms_suffix%"

# Default kit items given to every player on spawn (format: MATERIAL:AMOUNT:DAMAGE or MATERIAL:AMOUNT)
default-kit:
  - "STONE_SWORD:1"
  - "BOW:1"
  - "OAK_LOG:64"
  - "ARROW:16"
  - "GOLDEN_APPLE:16"
  - "BREAD:32"
  - "IRON_AXE:1"
  - "IRON_PICKAXE:1"

# Commands executed at game end. Placeholders: {winner_player}, {loser_player}, {kills}
# Use {winners} for all winners, {losers} for all losers
end-commands:
  per-winner:
    - "eco give {player} 100"
  per-kill:
    - "eco give {player} 10"

# Spectator settings
spectator-fly: true

# Particle cosmetic settings, permission: cores.cosmetic.particles
cosmetic-particle: FLAME
cosmetic-particle-radius: 1.0

# Alarm sound when core is attacked
core-alarm:
  enabled: true
  sound: "BLOCK_NOTE_BLOCK_PLING"
  volume: 1.0
  pitch: 0.5

core-mining-fatigue:
  amplifier: 0   # 0 = Fatigue I, 1 = II, 2 = III

# Spawn protection – enemies cannot enter this radius around the team spawns during a game.
# Block-breaking protection uses a separate radius (15 blocks, hardcoded above).
spawn-protection-radius: 10.0

# How many blocks around the two team-spawns to scan for chests when /cores enable runs.
# Increase if your map extends further than 200 blocks from the spawns.
chest-scan-padding: 200


# Messages (supports color codes with & and PlaceholderAPI)
messages:
  prefix: "&8[&6Cores&8] &r"
  no-permission: "&cYou don't have permission to do this."
  player-only: "&cThis command can only be used by players."
  chat-format: "{team}{prefix} {player}: &r{message}"
  arena-not-found: "&cArena '{arena}' not found."
  arena-already-exists: "&cAn arena with the name '{arena}' already exists."
  arena-created: "&aArena '{arena}' created successfully."
  arena-deleted: "&aArena '{arena}' deleted."
  arena-enabled: "&aArena '{arena}' has been enabled."
  arena-disabled: "&cArena '{arena}' has been disabled."
  lobby-set: "&aLobby location set."
  spawn-set: "&aSpawn for team {team} in arena '{arena}' set."
  waiting-spawn-set: "&aWaiting lobby spawn for arena '{arena}' set."
  spectator-spawn-set: "&aSpectator spawn for arena '{arena}' set."
  core-set: "&aCore for team {team} in arena '{arena}' set at your location."
  max-players-set: "&aMax players per team for arena '{arena}' set to {amount}."
  min-players-set: "&aMin players per team for arena '{arena}' set to {amount}."
  max-time-set: "&aMax game time for arena '{arena}' set to {seconds} seconds."
  join-arena: "{suffix}{player} &ejoined the game."
  leave-arena: "{suffix}{player} &eleft the game."
  not-in-arena: "&cYou are not in an arena."
  already-in-arena: "&cYou are already in an arena."
  arena-full: "&cThis arena is full."
  arena-not-enabled: "&cThis arena is not enabled or not set up yet."
  game-started: "&aThe game has started!"
  game-ended-winner: "&6Game Over! Team {team} has won!"
  game-ended-time: "&6Game Over! Time ran out! Team {team} wins!"
  game-ended-draw: "&6Game Over! It's a draw!"
  countdown-start: "&eThe game starts in &6{seconds} &eseconds!"
  countdown-waiting: "&eWaiting for more players... &7({current}/{min} per team)"
  countdown-waiting-scoreboard: "&eWaiting for players"
  player-killed: "{victimTeamColor}{victim} &7was killed by {killerTeamColor}{killer}&7." # Avaliable Placeholders: {victim}, {killer}, {victimTeamColor}, {killerTeamColor}, {victimPrefix}, {victimSuffix}, {killerPrefix}, {killerSuffix}
  team-joined: "&aYou joined team &r{team}&a."
  team-full: "&cThis team is already full. Teams must stay balanced."
  enemy-spawn-enter: "&cYou can`t enter an enemys spawn!"
  core-under-attack: "&c⚠ Your core is under attack!"
  core-destroyed: "&4☠ A core of team {team} has been destroyed!"
  core-destroyed-subtitle: "&rwas destroyed by {player}&r!"
  core-destroyed-enemy: "&aYou destroyed a core of team {team}!"
  spectator-join: "&7You are now spectating arena '{arena}'."
  game-already-started-spectator: "&7The game already started. You joined as spectator."
  start-countdown-set: "&aCountdown set to 5 seconds."
  forcestart: "&aForce starting the game..."
  not-enough-players: "&cNot enough players to start the game."
  invalid-usage: "&cUsage: {usage}"
  stats-header: "&6=== Your Cores Stats ==="
  stats-games-played: "&7Games Played: &f{value}"
  stats-wins: "&7Wins: &a{value}"
  stats-losses: "&7Losses: &c{value}"
  end-summary-header: "&6&l=== Game Summary ==="
  end-summary-winner: "&aWinner: Team {team}"
  end-summary-top-cores: "&7Top Core Destroyers:"
  end-summary-top-kills: "&7Top Killers:"
  end-summary-entry: "&7{rank}. {prefix} {player}&7: &e{value}"
  teleport-lobby-in: "&7Teleporting to lobby in &f{seconds} &7seconds..."
  leave-item-name: "&c&lLeave Game"
  leave-item-lore: "&7Click to leave the arena"
  team-selector-name: "&6&lTeam Selector"
  team-selector-lore: "&7Click to choose your team"
  team-red-name: "&c&lTeam Red"
  team-blue-name: "&9&lTeam Blue"
  team-red-lore: "&7Players: &f{current}/{max}"
  team-blue-lore: "&7Players: &f{current}/{max}"

# Scoreboard settings
scoreboard:
  waiting-title: "&6&lCores"
  waiting-lines:
    - "&7&m-----------"
    - "&fArena: &6{arena_name}"
    - ""
    - "&fPlayers: &e{player_count}&7/&e{max_players}"
    - ""
    - "&fCountdown:"
    - " &e{countdown}"
    - "&7&m-----------"
  game-title: "&6&lCores"
  game-lines:
    - "&7&m-----------"
    - "&fArena: &6{arena_name}"
    - ""
    - "&cTeam Red:"
    - " {red_core_1} &rLeft Core"
    - " {red_core_2} &rRight Core"
    - ""
    - "&1Team Blue:"
    - " {blue_core_1} &rLeft Core"
    - " {blue_core_2} &rLeft Core"
    - ""
    - "&fPlayers alive: &e{alive_count}"
    - "&fYour kills: &e{player_kills}"
    - ""
    - "&fTime left: &e{time_left}"
    - "&7&m-----------"
  core-status-intact: "&a✔"
  core-status-attacked: "&e⚠"
  core-status-destroyed: "&c✘"

# GUI settings
gui:
  main-title: "&6&lCores - Play"
  main-quick-join-name: "&a&lQuick Join"
  main-quick-join-lore:
    - "&7Join the arena with the most"
    - "&7players currently waiting."
  main-quick-join-material: "COMPASS"
  main-arena-select-name: "&6&lSelect Arena"
  main-arena-select-lore:
    - "&7Browse all available arenas"
    - "&7and choose one to join."
  main-arena-select-material: "BOOK"
  arena-select-title: "&6&lSelect Arena"
  arena-button-waiting-material: "GREEN_CONCRETE"
  arena-button-playing-material: "RED_CONCRETE"
  arena-button-name: "&f{arena_name}"
  arena-button-lore:
    - "&7Status: {status}"
    - "&7Players: &f{players}/{max_players}"
    - ""
    - "{join_hint}"
  arena-button-join-hint: "&aClick to join!"
  arena-button-spectate-hint: "&7Click to spectate."
  arena-status-waiting: "&aWaiting"
  arena-status-starting: "&eStarting"
  arena-status-playing: "&cPlaying"
  arena-status-disabled: "&8Disabled"
  back-button-name: "&c&lBack"
  back-button-material: "ARROW"

```

![gameplay](https://cdn.modrinth.com/data/25jgXOGh/images/47845cd2c761f1577a35747d53a64548546dddd2.png)
![Core destroyed](https://cdn.modrinth.com/data/25jgXOGh/images/56cbae36a6b614610f0e69b069975c30f14b5632.png)
