# Let It Die Borderless v0.1
<p align="center">
<img width="256" height="227" alt="Asset 1" src="https://github.com/user-attachments/assets/b7530990-1b40-49e0-bb71-f4b669167405" />
</p>
<img width="1683" height="431" alt="showcase example" src="https://github.com/user-attachments/assets/2ca22f73-6c45-4e7b-a784-e2d03061a179" />
<img width="438" height="353" alt="image" src="https://github.com/user-attachments/assets/51e82b80-cdb2-4ea7-876a-40c6ffafe6b8" />

Forces Let It Die into borderless windowed mode.
The game must already be in Windowed mode, not exclusive fullscreen.

## How it works

```
1. Set the game to Windowed
   (BrgGraphicsConfig.ini -> mbFullScreen=False).
2. Start the game and wait until it is past the launch screen.
3. Run this tool. Run as Administrator if the game is elevated.
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
Hide UI           default key is =
                  click the label to set another key
                  works while the window is hidden
Start minimized   ini only. start_minimized = true
                  starts hidden. press the hotkey to show it
Disable shortcut  disable_shortcut = true turns the hotkey off
```

## Game closes

```
Once the tool has seen the game running at least once,
it exits completely when the game closes.
Nothing is left in the background.
```

## Files

```
borderless_settings.ini   next to the program
borderless.lock           while running, removed on exit
UI_Assets                 UI background.webp
                          let it die cursor.webp
                          uncle glasses ready.webp
                          Lidico.ico
```

## Other helpful programs

```
Let It Die Local Saver        https://github.com/Grimfuldev/Let_it_Die_Local_Saver
Let It Die Launcher Manager   https://github.com/Grimfuldev/let_it_die_launcher_manager
```

## License and disclaimer

```
This is an unofficial fan tool. It is not affiliated with, authorized,
or endorsed by Grasshopper Manufacture or GungHo Online Entertainment.
LET IT DIE, its characters, names, and setting remain their property.
```
