# Predictive Input Buffer (Geode)

Delays button presses and releases by N physics ticks (1 tick = 1/240 s) and shows a live console.

Based on https://github.com/johanxwf/predictive-input-buffer, which is itself an unofficial
recreation of the original Predictive Input Buffer mod (no license file was found in that repo;
credit goes to its author). This is NOT the original developer's build and is not claimed to
behave identically to it.

## Stages (F6, in a level)

| Stage | All | Wave |
|-------|-----|------|
| 1 | 2 | 2 |
| 2 | 4 | 4 |
| 3 | 8 | 8 |
| 4 | 16 | 8 |
| OFF | raw input | raw input |

F6 cycles 2/2 -> 4/4 -> 8/8 -> 16/8 -> OFF -> 2/2. Key-repeat is ignored. F6 is only
intercepted while a level is active. Switching to OFF immediately applies queued inputs in order.

## Behaviour

- Press and release are both buffered; order is always preserved.
- Queue is cleared on death/restart, on leaving the level, and on loading a level.
- Only active in the real game (PlayLayer), not the editor.
- Wave delay is chosen per input from the player's current wave state.

## Build (no local setup)

1. Push this folder to a new GitHub repo.
2. Open Actions -> "Build Geode Mod" -> download the "Build Output" artifact.
3. Put `yourname.predictive-input-buffer.geode` in `Geometry Dash\geode\mods\`.

Local: install Geode CLI, `geode sdk install`, then `geode build`.

## Console

On startup the mod opens a console titled "Geode Predictive Input Buffer - Live Console"
(setting "Show live console", restart required). If Geode's own console is enabled, that existing
window is reused (a process can only have one console) and just gets the new title. The close
button is removed on the console the mod creates, since closing it would close the game.

## Before publishing

Replace `yourname` / `YourName` in `mod.json`.

## Not verified

Not compiled and not tested in-game. See the delivery notes for the list of risks.
