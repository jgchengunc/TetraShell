# TetraShell
TetraShell is an all-in-one Tetris quicksave hacking tool. You can use it to hack quicksaves while still making them seem legitimate and climb the leaderboard!

Demo: https://youtu.be/cgApaxgc814

## Usage
TetraShell will first prompt you to enter the path of a valid quicksave to start hacking. Then, you can use any of the following commands.

### Modify
Takes two arguments, the field to modify and the value to change it to.

Example: `modify score 1000`

### Rank
Takes two arguments, the metric to score on and the number of top games to display. Uploads the current quicksave to the central ranking database and prints the top players from the leaderboard.

Example: `rank score 5`

### Check
Indicates if the current quicksave is legitimate.

Example: `check`

### Recover
Takes one argument, the path to a disk image file to recover quicksaves from. Recovers and prints the list of recovered quicksave paths.

Example: `recover /playpen/a4/a4_disk.img`

### Switch
Allows the user to change the current quicksave being hacked. Checks whether the new quicksave is the same as the current one.

Example: `switch ./haxxed_quicksave.old.bin`

### Visualize
Shows the current state of the Tetris game board as it would be displayed in-game.

Example: `visualize`

### Info
Prints the following information about the current quicksave:
- Path
- Score
- Lines

Example: `info`

### Help
Prints help for a particular command.

Example: `help modify`

### Exit
Exits TetraShell. Can be used at any prompt.

Example: `exit`

## Features

### Short Commands
Allows commands to be abbreviated to the minimum number of unique distinguishable characters.

Example: `c`, `ch`, `che`, and `chec` all run the `check` command.

### Improved Prompt
Provides the following information in the prompt:
- Username
- Abbreviated name of current quicksave
- Score of current quicksave
- Lines of current quicksave

Example: `student@TShell[haxx...][1000/172]>`

### Quick-Rank
Allows the rank command to be called with one or zero arguments:
- If only the metric is specified, defaults to display 5 games
- If no arguments are specified, defaults to display 5 games by score

### Pretty-Recover
Provides a nice interface to view the `recover` command output and optionally allows the user to switch the current quicksave to one of the recovered ones.

Reprints the header every 50 quicksaves and prints the recovered quicksaves in order of recovery.

### Any Case
Accepts arguments in any combination of upper and lower case.

### Colors
The color of the arguments and resulting output oscillate along a gradient between blue and pink for consoles that support color.

## Implementation Decisions

### Argument Valiation
To provide accurate error messages, TetraShell itself handles most of the validation instead of delegating to the programs it calls.

### No Modulo on Color
To change colors, modulo is not used on the variable that keeps track of color. This prevents a jump in color when the variable overflows. 
