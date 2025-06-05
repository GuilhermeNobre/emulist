# EMULIST Directory Creator Documentation

## Overview
The **EMULIST Directory Creator** is a Go program designed to create a directory structure for organizing ROM files for various gaming platforms. It creates a root directory named `ROMs` and subdirectories for each gaming platform defined in a predefined map. Additionally, it generates a `systems.txt` file inside the `ROMs` directory, listing all platforms and their descriptions in a `key: value` format, sorted alphabetically.

## Purpose
The program simplifies the setup of a directory structure for emulators and ROMs by:
- Creating a root directory (`ROMs`) to store platform-specific subdirectories.
- Creating a subdirectory for each gaming platform listed in the `platform_list` map.
- Generating a `systems.txt` file that documents all platforms and their descriptions in a human-readable format.

## Prerequisites to modify
- **Go Runtime**: The program requires Go (version 1.13 or later recommended) to compile and run.
- **File System Permissions**: The user must have write permissions in the directory where the program is executed to create the `ROMs` directory and its contents.

## Installation and creation
1. Download from relases 
2. Windows Users
    1. Download .exe file and execute (not necessary administrator)
3. Linux 
    1. Donwload the .bin file and execute on terminal (not necessary special permissions)
4. MAC (coming soon)


## Usage
1. Run the program (`go run main.go` or `./emulist`).
2. The program displays a welcome message and prompts the user to press `Enter` to continue.
3. It creates the `ROMs` directory in the current working directory, followed by subdirectories for each platform listed in the `platform_list` map.
4. A `systems.txt` file is generated inside the `ROMs` directory, listing all platforms in alphabetical order.
5. The program outputs the status of each directory creation and confirms the creation of `systems.txt`.
6. The program pauses again, waiting for an `Enter` key press before exiting.

### Example Output
**Console Output**:
```
Welcome to the EMULIST Directory Creator!
This program will help you set up a directory structure for various gaming platforms.

It will also generate a systems.txt file listing all platforms and their descriptions.
Press ENTER to continue.
[User presses Enter]

Created directory: ROMs/3do
Created directory: ROMs/adam
Created directory: ROMs/amiga
...
Platform list written to systems.txt successfully. Thanks for using EMULIST Directory Creator!
[User presses Enter]
```

**File Output** (`ROMs/systems.txt`):
```
3do: 3DO Interactive Multiplayer
adam: Coleco Adam
amiga: Commodore Amiga
...
zxspectrum: Sinclair ZX Spectrum
```

## Code Structure
The program is written in Go and consists of a single `main.go` file with the following components:

### Package and Imports
- **Package**: `main`
- **Imports**:
  - `fmt`: For formatted I/O operations (e.g., printing to console and writing to files).
  - `os`: For file system operations (e.g., creating directories and files).
  - `sort`: For sorting the platform keys alphabetically.

### Constants and Variables
- **Constant**: `root_dir string = "ROMs"`
  - Defines the name of the root directory where platform subdirectories and `systems.txt` are created.
- **Variable**: `platform_list map[string]string`
  - A map containing platform keys (e.g., `"3do"`) and their descriptions (e.g., `"3DO Interactive Multiplayer"`).
  - Contains entries for various gaming platforms and emulators (e.g., Atari, Nintendo, Sega).

### Functions
- **welcome_message()**:
  - Displays a welcome message explaining the program's purpose.
  - Waits for the user to press `Enter` using `fmt.Scanln()` to continue execution.
- **main()**:
  - The entry point of the program.
  - Calls `welcome_message()` to display the initial prompt.
  - Creates the `ROMs` directory using `os.Mkdir`.
  - Extracts and sorts platform keys alphabetically using `sort.Strings`.
  - Creates a subdirectory for each platform key.
  - Creates and writes to `systems.txt` with platform keys and descriptions.
  - Handles errors during directory and file operations.
  - Pauses for user input before exiting.

### Error Handling
- **Directory Creation**:
  - Checks if the `ROMs` directory creation fails and exits if an error occurs (except if the directory already exists).
  - For platform subdirectories, errors (e.g., directory already exists) are logged, but the program continues processing other directories.
- **File Creation/Writing**:
  - Checks for errors when creating `systems.txt` and exits if creation fails.
  - Checks for errors when writing to `systems.txt` and exits if writing fails.
  - Ensures the file is closed using `defer file.Close()`.

## Platform List
The `platform_list` map contains entries for various gaming platforms and emulators, including:
- Consoles (e.g., Atari 2600, Nintendo SNES, Sega Genesis)
- Computers (e.g., Commodore 64, Apple II)
- Handhelds (e.g., Game Boy, PlayStation Portable)
- Arcade systems and emulators (e.g., MAME, ScummVM)
- Fantasy consoles (e.g., PICO-8, TIC-80)

The full list is defined in the `platform_list` map in `main.go`.

## Troubleshooting
- **Error: "Error creating directory: ..."**:
  - Ensure you have write permissions in the current directory.
  - Check if the directory already exists (non-fatal error; the program continues).
- **Error: "Error creating systems.txt: ..."**:
  - Verify write permissions in the `ROMs` directory.
  - Ensure there is enough disk space.
- **Program Hangs**: If the program seems stuck, ensure you press `Enter` when prompted.

## License
This program is licensed under the **GNU General Public License v3.0 (GPL-3.0)**. You are free to use, modify, and distribute this software under the terms of the GPL-3.0 license. See the [LICENSE](LICENSE) file or visit [https://www.gnu.org/licenses/gpl-3.0.html](https://www.gnu.org/licenses/gpl-3.0.html) for full details.

## Author
This program was created to assist in organizing ROM files for emulator users. For questions or contributions, please contact me via the GitHub repository or open a issue.