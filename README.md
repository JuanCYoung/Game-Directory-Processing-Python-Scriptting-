# Game-Directory-Processing-Python-Scriptting-
# Game Directory Processor

## Overview

This project is a personal Python-based tool for processing directories containing game source code using Python Script. The tool performs the following tasks:

1. **Identifies game directories**: Searches for directories containing a specific pattern (e.g., `game`) within a source directory.
2. **Renames directories**: Strips specific substrings (e.g., `_game`) from directory names.
3. **Copies directories**: Creates a target directory and copies the identified game directories into it.
4. **Compiles game code**: Identifies Go source files (`.go`) in each directory and compiles them using the `go build` command.
5. **Generates metadata**: Creates a `metadata.json` file in the target directory, containing the names of the processed game directories and the total count.

## Features

- Automated directory processing and renaming.
- Handles compilation of Go code within game directories.
- Generates metadata for easy tracking of processed directories.
- Includes error handling and overwriting logic for directory operations.

## Setup and Usage

### Running the Script
To execute the script, run the following command from the terminal:

```bash
python3 script_name.py <source_directory> <target_directory>
```

Replace `<source_directory>` with the path to the source folder containing game directories and `<target_directory>` with the destination folder where processed directories and metadata will be saved.

### Example

Suppose your source directory structure looks like this:

```
source/
  game_1_game/
    main.go
  game_2_game/
    game.go
```

Run the script:

```bash
python3 script_name.py source target
```

After execution, the target directory will contain:

```
target/
  game_1/
    main.go
    <compiled binary>
  game_2/
    game.go
    <compiled binary>
  metadata.json
```

### Metadata File
The `metadata.json` file contains information like this:

```json
{
  "gameNames": ["game_1", "game_2"],
  "numberOfGames": 2
}
```

## Key Functions

### `find_all_game_dirs(source)`
Finds all directories in the source path matching the `GAME_DIR_PATTERN` (default: `game`).

### `get_name_from_paths(paths, to_strip)`
Strips a specified substring (e.g., `_game`) from directory names.

### `create_dir(path)`
Creates a directory at the given path if it does not already exist.

### `copy_and_overwrite(source, dest)`
Copies a directory to a target location, overwriting any existing content.

### `compile_game_code(path)`
Searches for `.go` files in the directory and compiles them using `go build`.

### `make_json_metadata_file(path, game_dirs)`
Generates a JSON metadata file listing the processed game directories and their count.

## Error Handling

- Raises an exception if the script is run without exactly two arguments.
- Ensures directories are created only if they do not already exist.
- Removes and overwrites directories during the copy operation to avoid conflicts.

## Contributing

Contributions are welcome! Feel free to submit issues or pull requests for bug fixes or new features.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

Enjoy processing your game directories efficiently!

