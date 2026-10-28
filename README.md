# Let It Die Borderless v0.4
<p align="center">
<img width="256" height="256" alt="Lidico" src="https://github.com/user-attachments/assets/6aeb57c7-4269-4940-a4e2-9ffa84fb56d0" />
</p>
<img width="1683" height="431" alt="showcase example" src="https://github.com/user-attachments/assets/602788f3-2e40-43bf-bd12-0b952601df13" />
<img width="1052" height="638" alt="image" src="https://github.com/user-attachments/assets/4f07ec34-cce3-4363-a102-5a3bf10757a7" />

**v0.4**. Forces Let It Die into borderless windowed mode, and includes an optional Reticle Maker & Patcher.
The game must already be in Windowed mode, not exclusive fullscreen.

## How it works

```
1. Set the game to Windowed
2. Start the game.
3. Run this tool.
4. Pick an aspect and click Make Borderless.
Done.
Stop Borderless restores the original window.
```

## Aspect

```
Fill Screen     cover the whole monitor
16:9, 16:10...  largest centered area of that ratio
Native size     keep the game's current pixel size, centered
```

When the game does not fill the whole monitor (any choice but Fill Screen) the rest of
the monitor is covered with black, behind the game.

In windowed mode the game draws its picture at a size that fits the screen with its
window frame (for example 1850x1041 on a 1920x1080 monitor). Native size shows it
1:1, which keeps small details like a one pixel reticle outline sharp. Fill Screen
stretches it to the monitor, which makes such details jagged displaced.

## Options

```
Auto Borderless   apply a few seconds after the game window is found
Hide UI           no shortcut by default
                  click the label to set a key
                  right click the label to remove the shortcut
                  still works while the window is hidden
Start minimized   ini only. start_minimized = true
                  starts hidden. press the hotkey to show it
                  ignored when there is no shortcut
Disable shortcut  disable_shortcut = true turns the hotkey off
Close with game   close_with_game = false (default) keeps the tool running when
                  the game closes and waits for the next start. true closes it
                  5 seconds after the game closes, with a popup (in the Reticle
                  window too) and a Cancel button that keeps it running
```

## Borderless stays on

```
Once borderless is on it stays on until you press Stop Borderless.
When the game resets or re-creates its window (main menu, loading screens)
the tool applies borderless again by itself.
A window that is already borderless (for example from an earlier run of
the tool) is taken over as it is: Make Borderless stays greyed and Stop
Borderless restores the original window.
When the game process has been gone for 1.5 seconds, borderless is switched off
and, if close_with_game = true, the tool exits after a 5 second warning with a
Cancel button (otherwise it waits for the next start).
```

## Reticle Maker

Opens from the Reticle button. Makes a custom reticle and bakes it into the game's HUD.

```
How it works
  The reticle image is painted into the HUD texture (UI_HUD_SF.upk), into the
  cell of the stock reticle. Its position is set in BrgGameBase.upk
  (Reticle Deviation x / y). Nothing runs while you play.
  Biggest reticle: 58 x 58 stored pixels.
  Anything outside that square is cropped, and every preview shows it cropped.

Setup
  Browse            pick steam.exe so the game files are found
  Unlock SHA        turns off the game's file check. Safe copies are saved
                    next to the game files as <file>.<buildid>.backup
  Patch Reticle    asks first (tick "Don't show again" to skip it next time),
                    then writes UI_HUD_SF.upk (the picture) and BrgGameBase.upk
                    (the deviation).
                    Right click: puts the original HUD and BrgGameBase back
                    (the SHA stays unlocked)
  Original Deviate  keeps the original reticle: puts the HUD back if it was
                    modified and only modifies BrgGameBase.upk to move it by
                    the Reticle Deviation.
                    Right click: puts the original BrgGameBase back only
                    Both buttons are greyed while the game runs, while the SHA
                    state is being looked up, and until steam.exe is browsed
                    and the SHA unlocked
  Restore SHA       puts the original game program back, and the HUD and
                    BrgGameBase too if they are still modified (they may
                    already have been restored), and the game's engine ini
                    (SteamPCRelease-BrgEngine.ini, which the game rewrites every
                    time it runs and which makes the game refuse to start),
                    and deletes the backups
                    (greyed out when no backup for this game version exists)
  Reticle Deviation x / y  (in the preview popup, with sliders up to 200 and neg.)
                    how far the reticle is moved. Raw HUD units
                    (a 3840 x 2160 layout, scaled to your screen), -1000 to 1000.
                    0 / 0 = the stock position. Adjust it with Take photo
  Patch Reticle also adds a small fixed deviation of its own, so your reticle
  is centred where the stock reticle was (the stock one is not centred in its
  picture cell). Original Deviate does not
  add it.
  A game update makes the old backups stale: they are replaced by fresh ones
  from the new clean files.
  Advanced: "auto_reapply": true in reticle_config.json redoes what a game
  update undid, once when this program starts (game closed): unlocks SHA again
  and repeats the last Patch Reticle, or the last Original Deviate (then the
  HUD is left alone). Nothing is redone after a right click restore.

Making a reticle
  Outer / Center    click a box to pick images (one per folder).
                    The boxes and the catalog preview show the real 58 x 58 reticle area
  Preview           click it for the preview popup: actual size on black or
                    white, or over a picture of the game, with Save Reticle,
                    Import Reticle and Take photo
```

### Deviation depends on resolution

```
The Reticle Deviation that lines the reticle up is not universal. It depends
on the resolution of the game screen AND on the resolution of your monitor.
Change either one and the same numbers put the reticle somewhere else, so
check the deviation again in the preview popup (take a new photo) every time you
change the game resolution or the monitor resolution.
Saved photos keep the deviation metadata stored so those get mounted automatically
when it detect you are playing on a game resolution and monitor resolution that match
a photo already taken.
```

### If something stops working

```
"The game has been modified and cannot launch" (or similar)
    The game's SHA check got locked again. Press Unlock SHA again.
The reticle went back to the original deviation
    A game update or Steam's "Verify integrity of game files" restored the
    files. Patch Reticle / Original Deviate again (auto_reapply can do it
    for you when this program starts).
The game looks broken, the game devs probably modified the target files in an update
rendering this program outdated.
```

### Take photo

```
In the preview popup choose the aim button (mouse key, keyboard key, joystick
button) and press Take photo (it becomes Cancel while waiting, Retake photo
when a photo is already mounted, and it is cancelled when you leave the popup).
Go to the game: a countdown banner shows and holding the aim button for the
Timer seconds (default 2) takes a picture of the game.

A photo can only be taken when
  - borderless is ON (the borderless tool tells the Reticle window),
  - the game is running, and
  - BrgGameBase.upk has Reticle Deviation 0 / 0 (restore it, or set 0 / 0 and
    use Original Deviate). Otherwise the button is grey.

Photos are stored in Reticles\_Current\_InGameAim, named
<game resolution setting>_<screen width>x<screen height>, e.g. 12_2560x1440.webp.
The game resolution setting is mResolutionType in
<game>\BrgGame\Config\BrgGraphicsConfig.ini. Each combination of game
resolution and screen resolution has its own photo; the preview mounts the one
that fits when it opens, and shows none when there is none. If either
resolution changes while the program is open it says
"Current in-game resolution and/or computer resolution changed, new photo needed".
_InGameAim folder is not offered as a reticle.

Spacebar cycles black / white / photo. In photo view hold the left mouse button to
drag the picture around under the reticle, and hold the right mouse button to
move the reticle: the numbers follow it (limit 200).
Patch Reticle and Original Deviate store the deviation x / y inside the mounted
photo (_InGameAim\<name>.webp). Whenever that photo is mounted again by opening preview,
those values are put back in the fields, so each photo remembers the deviation it needs.
The Return deviation button (next to the aim inputs, greyed out without a photo) puts
the values stored in the mounted photo back into the fields at any time.
```

## Files

```
borderless_settings.ini   next to the program
borderless.lock           while running, removed on exit
borderless_status.json    while running: whether borderless is on (photos need it)
reticle_config.json       Reticle Maker settings
Reticles\                 reticle images and their Section_configs.json
<game folder>             UI_HUD_SF.upk.<buildid>.backup
                          BrgGameBase.upk.<buildid>.backup
                          BrgGame-Steam.exe.<buildid>.backup
                          BrgGame\Config\SteamPCRelease-BrgEngine.ini.<buildid>.backup
UI_Assets                 UI background.webp
                          let it die cursor.webp
                          uncle glasses ready.webp
                          Lidico.ico
                          Boxes\ (joystick button .png files)
```

## License and disclaimer

```
This is an unofficial fan tool with fanmade assets. It is not affiliated with, authorized,
or endorsed by Grasshopper Manufacture or GungHo Online Entertainment.
LET IT DIE, its characters, names, and setting remain their property.

This program modifies game files (it keeps a backup of each one in the game folder,
and Restore SHA puts them back). Use it at your own risk. It is provided as is,
without any warranty, and the author is not responsible for any damage or data loss
that may result from using it.
Keep your own backup of your game files and saves.
```

## Credits

Huge thanks to SES7 for the SHA Check remover: https://gamebanana.com/tools/24197
Without it, the reticle swap tool wouldn't be possible.

## Other helpful programs

- [https://github.com/Grimfuldev/let_it_die_launcher_manager](https://github.com/Grimfuldev/let_it_die_launcher_manager/releases/latest)
- [https://github.com/Grimfuldev/Let_it_Die_Local_Saver](https://github.com/Grimfuldev/Let_it_Die_Local_Saver/releases/latest)
- [https://github.com/Grimfuldev/let_it_die_rotations_and_seasons](https://github.com/Grimfuldev/let_it_die_rotations_and_seasons/releases/latest)
