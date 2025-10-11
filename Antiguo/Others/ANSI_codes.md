
# ANSI Escape Codes
This codes are used to control the cursor location, color, font, styling and another options on terminals.
They can be used as any other text variable.
[More info.](https://gist.github.com/fnky/458719343aabd01cfb17a3a4f7296797)

## Example
```Python
# Python example of ANSI code usage.
regularRed = "\033[0;31m"
reset = "\033[0m"

print(regularRed +"Hello World!" + reset)
```

## Format
```Bash
\33[ <Values> m
```

- Allways start with `\33[` and end with `m` .
- We must replace values with the format.
- Several can be specified separed by commas.

## Erase Functions

| Value | ESC Code Sequence | Description                               |
| ----- | :---------------- | :---------------------------------------- |
| J     | `\33[J`           | erase in display (same as ``ESC\[0J``)    |
| 0J    | `\33[0J`          | erase from cursor until end of screen     |
| 1J    | `\33[1J`          | erase from cursor to beginning of screen  |
| 2J    | `\33[2J`          | erase entire screen                       |
| 3J    | `\33[3J`          | erase saved lines                         |
| K     | `\33[K`           | erase in line (same as ``ESC\[0K``)       |
| 0K    | `\33[0K`          | erase from cursor to end of line          |
| 1K    | `\33[1K`          | erase start of line to the cursor         |
| 2K    | `\33[2K`          | erase the entire line                     |

### Text format Modes
| Value | Example Sequence | Reset Sequence | Description               |
| ----- |------------------|----------------|---------------------------|
| 0     | `\33[0m`         |                | reset all modes           |
| 1     | `\33[1m`         | `\33[22m`      | set bold mode.            |
| 2     | `\33[2m`         | `\33[22m`      | set dim/faint mode.       |
| 3     | `\33[3m`         | `\33[23m`      | set italic mode.          |
| 4     | `\33[4m`         | `\33[24m`      | set underline mode.       |
| 5     | `\33[5m`         | `\33[25m`      | set slow blinking mode    |
| 6     | `\33[6m`         | `\33[26m`      | set fast blinking mode    |
| 7     | `\33[7m`         | `\33[27m`      | set inverse/reverse mode  |
| 8     | `\33[8m`         | `\33[28m`      | set hidden/invisible mode |
| 9     | `\33[9m`         | `\33[29m`      | set strikethrough mode.   |

### Colors
| Color Name | Foreground Color Code | Background Color Code |
| ---------- | --------------------- | --------------------- |
| Black      | `30`                  | `40`                  |
| Red        | `31`                  | `41`                  |
| Green      | `32`                  | `42`                  |
| Yellow     | `33`                  | `43`                  |
| Blue       | `34`                  | `44`                  |
| Magenta    | `35`                  | `45`                  |
| Cyan       | `36`                  | `46`                  |
| White      | `37`                  | `47`                  |
| Default    | `39`                  | `49`                  |
| Reset      | `0`                   | `0`                   |