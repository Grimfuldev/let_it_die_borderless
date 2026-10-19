# Let It Die Borderless
<p align="center">
<img width="256" height="256" alt="Lidico" src="https://github.com/user-attachments/assets/5c08143f-2221-4469-90a9-509d494af677" />
</p>
<img width="428" height="277" alt="image" src="https://github.com/user-attachments/assets/56cb7909-ce34-4078-92a2-bd46e1b65426" />

Forces Let It Die into borderless windowed mode.
The game must already be in Windowed mode, not exclusive fullscreen.

## How it works

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
Hide UI           default key is =
                  click the label to set another key
                  still works while the window is hidden
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

## License and disclaimer

```
This is an unofficial fan tool with fanmade assets. It is not affiliated with, authorized,
or endorsed by Grasshopper Manufacture or GungHo Online Entertainment.
LET IT DIE, its characters, names, and setting remain their property.
```

## Other helpful programs

- [https://github.com/Grimfuldev/let_it_die_launcher_manager](https://github.com/Grimfuldev/let_it_die_launcher_manager)
- [https://github.com/Grimfuldev/Let_it_Die_Local_Saver](https://github.com/Grimfuldev/Let_it_Die_Local_Saver)
- [https://github.com/Grimfuldev/let_it_die_rotations_and_seasons](https://github.com/Grimfuldev/let_it_die_rotations_and_seasons)
