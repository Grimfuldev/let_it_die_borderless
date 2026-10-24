# Let It Die Borderless v0.2
<p align="center">
<img width="256" height="256" alt="Lidico" src="https://github.com/user-attachments/assets/1c51f61f-d27c-4924-8156-5446a7008bea" />
</p>
<img width="1683" height="431" alt="showcase example" src="https://github.com/user-attachments/assets/2ca22f73-6c45-4e7b-a784-e2d03061a179" />
<img width="436" height="328" alt="image" src="https://github.com/user-attachments/assets/80804e19-32ac-4e8a-bb06-de55f59409d0" />
<img width="591" height="653" alt="image" src="https://github.com/user-attachments/assets/2cf83250-b66f-4827-8aad-434c41923d73" />

**v0.2**. Forces Let It Die into borderless windowed mode, and includes the Reticle Maker.
The game must already be in Windowed mode, not exclusive fullscreen.

## How Borderless works

```
1. Set the game to Windowed
2. Start the game.
3. Run this tool.
4. Pick an aspect and click Make Borderless.
5. Stop Borderless restores the original window.
```

## Aspect

```
Fill Screen     cover the whole monitor
16:9, 16:10...  largest centered area of that ratio
Native size     keep the game's current pixel size, centered
```

## Options

```
Auto Borderless   apply a few seconds after the game window is found
Hide UI           no shortcut by default, click the label to set a key
                  right click the label to remove the shortcut
                  still works while the window is hidden
Start minimized   ini only. start_minimized = true
                  starts hidden. press the hotkey to show it
                  ignored when there is no shortcut
Disable shortcut  disable_shortcut = true turns the hotkey off
```

## One copy at a time

```
Running the program again closes the copy that is already running
(and its Reticle window) and the new one takes over.
```

## Game closes

```
Once the tool has seen the game running at least once,
it exits completely when the game closes, nothing is left in the background.
```

## Reticle Maker

Opens from the Reticle button in Borderless UI. Makes a custom reticle and draws it in the game.

```
Setup
  Browse            pick steam.exe so the game files are found
  Unlock SHA        Requires the original .EXE game files to work.
                    turns off the game's file check. Safe copies are saved
                    next to the game files as <file>.<buildid>.backup
  Inject Mark       Requires the original HUD game files to work.
                    puts the VALUE px mark into UI_HUD_SF.upk (Reinject Mark if already done)
  Start Adjust      hold your aim button in game to calibrate the mark,
                    if you change your game scale or window mode, you will have to do it again.
  Restore SHA       puts both original files back and deletes the backups
                    (greyed out when no backup for this game version exists)
  A game update makes the old backups stale: they are replaced by fresh ones
  from the new clean files.
  Advanced: "auto_unlock_sha_mark": true in reticle_config.json redoes what a game
  update undid, once when this program starts (game closed): unlocks SHA again
  and reinjects the last mark (color / size of the last Inject Mark).

Making a reticle
  Outer / Center    click a box to pick images (one per folder)
  Preview           click it: actual size on black or white (checkbox), with
                    Save Reticle and Import Reticle
                    Space cycles black / white / game view (see below)
  Apply             writes the reticle to Reticles\_Current
```

### Reticles folder

```
Reticles\_Outer, Reticles\_Center   put your own folders and images here (.webp / .png)
_Default folders                    restored if deleted, with Plus.png / Dot.png
Section_configs.json                each folder keeps its own options, never its subfolders'
```

### Catalog options (per folder, saved when you press Accept)

```
Focus             the folder the options below edit (one at a time)
Both              Color, Opacity, Size px, Stretch X/Y %
Outer only        Dupe, Rotate Dupe, Rotate All, Spread
Center only       Rotate, Displace X/Y
Sliders           0-100 with a neg. checkbox
Reset focused     back to defaults        Copy / Paste   move options between folders
disable grid      hides the guide grid
```

Order: dupe / rotate / spread, color and opacity, size, stretch, then displace.

### Main window

```
Scale Adjust      global size of the final image (slider + neg.)
Override Color    one more hue change over everything (checkbox)
Subtract Opacity  takes opacity off every pixel (100 = invisible)
Post Outline      soft black outline, on by default. Width, blur and opacity
                  are in reticle_config.json (outline_*, original values noted)
```

### Presets and saved reticles

```
Save Preset       exports every folder config and all settings to a json
Import Preset     loads it (anything not found is ignored)
Right click       Import Preset = reset everything to defaults (asks first)
Save Reticle      saves the reticle to _Outer as <name>.config.webp with how it
                  was built stored inside
Import Reticle    pick a .config image: its images and options come back and
                  it is applied ("reticle without metadata" if it has none)
```

### Game view

```
When the Reticle window is shown with the hotkey while the game is in front,
one picture of the game screen is kept in memory (never saved to disk).
In the preview popup press Space to see the reticle over it. The reticle
stays in the middle; hold the mouse button and drag to move the picture
around (it stops at the picture's edges and returns to the centre when you
let go). Esc or Space leaves it. The picture is dropped when the Reticle
window is hidden.
```

## Files

```
borderless_settings.ini   next to the program
borderless.lock           while running, removed on exit
reticle_config.json       Reticle Maker settings
Reticles\                 reticle images and their Section_configs.json
<game folder>             UI_HUD_SF.upk.<buildid>.backup
                          BrgGame-Steam.exe.<buildid>.backup
UI_Assets                 UI background.webp
                          let it die cursor.webp
                          uncle glasses ready.webp
                          Lidico.ico
                          Boxes\ (joystick button .png files)
```
`
## License and disclaimer

```
This is an unofficial fan tool with fanmade assets. It is not affiliated with, authorized,
or endorsed by Grasshopper Manufacture or GungHo Online Entertainment.
LET IT DIE, its characters, names, and setting remain their property.

This program modifies game files, it keeps a backup of the modified ones in the game folder as well. Use it at your own risk. It is provided as is, without any warranty, and the author is not responsible for any damage, data loss,
game malfunction, or account action, including bans, that may result from using it.
```

## Credits

Huge thanks to SES7 for the SHA Check remover: https://gamebanana.com/tools/24197 
Without it, the reticle swap tool wouldn't be possible. (This program uses its own reversible built-in version of that).

## Other helpful programs

- [https://github.com/Grimfuldev/let_it_die_launcher_manager](https://github.com/Grimfuldev/let_it_die_launcher_manager/releases/latest)
- [https://github.com/Grimfuldev/Let_it_Die_Local_Saver](https://github.com/Grimfuldev/Let_it_Die_Local_Saver/releases/latest)
- [https://github.com/Grimfuldev/let_it_die_rotations_and_seasons](https://github.com/Grimfuldev/let_it_die_rotations_and_seasons/releases/latest)
