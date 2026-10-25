# Let It Die Borderless v0.1
<p align="center">
<img width="256" height="256" alt="Lidico" src="https://github.com/user-attachments/assets/c5483747-b0b1-496b-a6fa-10bee8668cb5" />
</p>
<img width="428" height="277" alt="example ui" src="https://github.com/user-attachments/assets/eada469f-e9b7-497b-83e3-0650c2053999" />

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
