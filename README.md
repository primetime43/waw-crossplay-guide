# WaW Crossplay Guide

World at War multiplayer setup for PS3, RPCS3, and Xenia Netplay.

This guide connects *Call of Duty: World at War* competitive multiplayer to a
community-run recreation of the game's Demonware online services. It covers
physical PS3, RPCS3, and the Xbox 360 multiplayer game in **Xenia Netplay**.
It also includes a setup tool and launcher for Xenia Netplay.

**Live server status:** [WaW server dashboard](http://157.230.65.227:8081/dashboard/)
— check players online, active games, open sessions, and recent player activity.

For PS3 and RPCS3, install game update **1.07** before connecting. This is the
latest update for the releases currently used with this server; other regional
versions have not yet been verified.

**Jump to:** [Physical PS3](#physical-ps3) · [RPCS3](#rpcs3) ·
[Xenia Netplay](#xenia-netplay) · [Cross-platform proof](#cross-platform-proof) ·
[Quick fixes](#quick-fixes)

| Platform | Server setting |
| --- | --- |
| Physical PS3 | DNS `67.222.156.250` |
| RPCS3 | DNS `67.222.156.250` |
| Xenia Netplay | API `http://157.230.65.227:8081/xenia/` |

## Physical PS3

1. Open **Settings → Network Settings → Internet Connection Settings**.
2. Keep your normal IP and connection settings, but set **DNS Setting** to
   **Manual**.
3. Set **Primary DNS** to `67.222.156.250`.
4. Do not configure a public secondary DNS; it can bypass the WaW server records.
5. Save the settings and test the connection.
6. Fully restart *World at War*, select **Multiplayer**, then **Play Online**.

No patched game file or hosts-file change is needed. A fresh connection can
take up to three automatic attempts.

## RPCS3

1. Sign in to RPCN and close *World at War*.
2. Right-click *World at War* in RPCS3 and open its custom configuration.
3. Under **Network**, set **Network Status** to **Connected** and
   **PSN Status** to **RPCN**.
4. Set **DNS** to `67.222.156.250`.
5. Paste this entire line into **IP/Hosts switches**:

   ```text
   cod5-ps3.auth.mmp3.demonware.net==157.230.65.227&&cod5-ps3-live.lsg.mmp3.demonware.net==157.230.65.227&&cod5-ps3-dev.lsg.mmp3.demonware.net==157.230.65.227&&cod5-ps3-cert.lsg.mmp3.demonware.net==157.230.65.227&&stun.us.demonware.net==157.230.65.227&&stun.eu.demonware.net==157.230.65.227
   ```

6. Save the custom configuration, fully exit and restart RPCS3, then open
   multiplayer and select
   **Play Online**.

Use a different RPCN account for each player.

## Xenia Netplay

This requires the
[official Xenia Canary Netplay release](https://github.com/AdrianCassar/xenia-canary/releases/latest).
Standard Xenia builds are not supported by the setup launcher.

1. Keep `xenia_canary_netplay.exe`, `portable.txt`, and
   `xenia-canary-netplay.config.toml` together. Open Xenia once, then close it.
2. Download this repository and keep its four launcher files together.
3. Run `configure_waw_xenia.bat`.
4. Accept the default server or enter:

   ```text
   http://157.230.65.227:8081/xenia/
   ```

5. Select the Xenia Netplay executable and your WaW multiplayer
   `default_mp.xex`.
6. Run `launch_waw_xenia.bat` whenever you want to play.

The launcher backs up the Xenia configuration before changing its Netplay API
settings. Use the API URL above—not the PS3 DNS address.

## Cross-platform proof

These screenshots demonstrate **cross-platform multiplayer between RPCS3
(PS3) and Xenia Netplay (Xbox 360)** in *World at War*. Players on the two
emulators join the same lobby and play together in the same match, with both
players visible on each emulator's in-game scoreboard.
RPCS3 is on the left and Xenia Netplay is on the right in the side-by-side images.

![Cross-platform World at War match between RPCS3 (PS3) and Xenia Netplay (Xbox 360)](docs/screenshots/rpcs3-xenia-gameplay.png)

![RPCS3 and Xenia Netplay scoreboards showing the same two players in a cross-platform match](docs/screenshots/rpcs3-xenia-scoreboard.png)

<details>
<summary>More lobby, matchmaking, and gameplay screenshots</summary>

Cross-platform gameplay on Castle between RPCS3 and Xenia Netplay:

![World at War on Castle in RPCS3 and Xenia Netplay](docs/screenshots/rpcs3-xenia-castle-gameplay.png)

Shared cross-platform Team Deathmatch lobby on Castle with both players and the match countdown:

![RPCS3 and Xenia Netplay in a two-player Castle lobby](docs/screenshots/rpcs3-xenia-castle-lobby.png)

Matchmaking on both emulators, each showing 2/12 players:

![RPCS3 and Xenia Netplay matchmaking screens with two players](docs/screenshots/rpcs3-xenia-matchmaking.png)

RPCS3 party showing two players:

![World at War party in RPCS3 with two players](docs/screenshots/rpcs3-party.png)

</details>

## Quick fixes

| Problem | Check |
| --- | --- |
| PS3 shows Error 33 | Confirm the custom DNS is primary, remove any public secondary DNS, and restart the game. |
| Stuck on **Downloading Game Settings** | Restart the game or emulator so it performs a fresh server lookup. |
| Lobby appears but **Getting match quality** never finishes | Confirm PS3 or RPCS3 is using DNS `67.222.156.250`. In RPCS3, clear any old **IP/Hosts switches** and fully restart the emulator. |
| RPCS3 ignores new settings | Fully exit RPCS3; restarting only the game can retain old network results. |
| Xenia setup refuses to run | Close every Xenia process and confirm you selected a portable Xenia Netplay installation. |

Physical Xbox 360 setup is not included because its connection path is not yet figured out.

This repository does not provide game files, emulator builds, online profiles, or title updates.
