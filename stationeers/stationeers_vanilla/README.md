# Stationeers

Construct and manage your own space station either by yourself in singleplayer or with friends online. Fully functioning atmospherics, science, power, engineering, medical, logic, and agricultural systems. Explore to find asteroids and construct elaborate factories to harvest your resources.

## Server CLI changed in the September 2025 terrain update

Pre-update servers used `-loadlatest <save> <worldname>`. The current server uses `-file start "<save>" <WorldId> <Difficulty> <StartCondition> <StartLocation>`. Old eggs that pass the legacy flags fail to boot. If you are running a save from before the terrain update, use the `preterrain` SteamCMD beta branch via the `SRCDS_BETAID` variable.

## Docker image requirement

`libRakNetDLL.so` requires GLIBC ≥ 2.38 and GLIBCXX ≥ 3.4.31. The Ubuntu 22.04 yolk is too old. This egg uses `ghcr.io/ptero-eggs/steamcmd:ubuntu_24.04` (Ubuntu 24.04 — GLIBC 2.39, GLIBCXX 3.4.32). If you change the image, pick one based on Debian 13 (trixie) or Ubuntu 24.04+.

## Recommended server settings

| Resource | Recommended |
|----------|-------------|
| RAM      | 4 GB minimum, 8 GB for 10+ players |
| CPU      | 2 dedicated cores |
| Storage  | 5 GB (game ~2 GB + saves) |

## Server Ports

| Port           | Default | Variable      |
|----------------|---------|---------------|
| Game           | 27500   | `SERVER_PORT` |
| Steam Query    | 27015   | `UPDATE_PORT` |

## Variables

| Variable             | Default                    | Notes |
|----------------------|----------------------------|-------|
| `SERVER_NAME`        | `Pterodactyl Hosted Server`| Display name in the server browser |
| `SAVE_NAME`          | `world`                    | World save folder name |
| `WORLD_ID`           | `Mars2`                    | `Lunar, Mars2, Europa3, MimasHerschel, Vulcan, Venus, Tutorial1, Tutorial2, Tutorial3, Airlock, FurnaceBasics, Manufacturing` |
| `DIFFICULTY`         | `Normal`                   | `Creative, Easy, Normal, Stationeer` (blank for tutorials) |
| `START_CONDITION`    | `DefaultStart`             | `DefaultStart, DefaultStartCommunity, Brutal, BrutalCommunity` (blank for tutorials) |
| `START_LOCATION`     | `MarsSpawnButchersFlat`    | Map-specific spawn ID (see wiki); blank for tutorials |
| `MAX_PLAYERS`        | `10`                       | 1–30 |
| `SERVER_PASSWD`      | *(empty)*                  | Blank = public |
| `SERVER_AUTH_SECRET` | `changechange`             | Change before going public |
| `AUTOSAVE`           | `true`                     | |
| `SAVE_INTERVAL`      | `300`                      | Seconds; minimum 60 |
| `AUTO_PAUSE`         | `false`                    | Pause when empty |
| `UPNP`               | `false`                    | Router must support UPnP |
| `USE_STEAM_P2_P`     | `false`                    | Keep disabled |
| `UPDATE_PORT`        | `27015`                    | Steam query port |
| `SRCDS_APPID`        | `600760`                   | Stationeers Dedicated Server |
| `AUTO_UPDATE`        | `1`                        | `1` = update on boot |
| `SRCDS_BETAID`       | *(empty)*                  | e.g., `preterrain` for legacy saves |

`START_LOCATION` is map-specific. Authoritative list lives at <https://stationeers-wiki.com/Dedicated_Server_Guide>.

## Updating notes

The runtime image auto-runs SteamCMD app update on boot when `AUTO_UPDATE=1`. Set `0` to pin a version. Use `SRCDS_BETAID=preterrain` to stay on the pre-update branch.

## Authors / Contributors

- eggs@goover.dev
- Updated for post-2025 terrain-update CLI, Ubuntu 24.04 base image, and AMP-aligned startup args.
