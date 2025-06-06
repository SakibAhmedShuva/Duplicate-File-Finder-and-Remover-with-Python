# Duplicate File Finder and Remover with Python

A powerful and flexible Python tool for finding and removing duplicate files based on filename and/or file size. Perfect for cleaning up directories, organizing file systems, and reclaiming disk space.

## Features

- **Flexible Matching**: Find duplicates by filename only or by both filename and size
- **Recursive Search**: Searches through all subdirectories automatically
- **Multiple Keep Strategies**: Choose which files to keep when removing duplicates
- **Safe Operations**: Preview mode and confirmation prompts prevent accidental deletions
- **Detailed Reports**: Shows file paths, sizes, and potential space savings
- **Error Handling**: Gracefully handles file access issues and permission errors
- **Jupyter Notebook Ready**: Designed for interactive use in notebooks

## Installation

Clone this repository:

```bash
git clone https://github.com/SakibAhmedShuva/Duplicate-File-Finder-and-Remover-with-Python.git
cd Duplicate-File-Finder-and-Remover-with-Python
```

No additional dependencies required - uses only Python standard library.

## Quick Start

### Basic Usage

```python
# Configuration
SAME_NAME = True   # Match by filename
SAME_SIZE = True   # Also match by file size
INPUT_PATH = "/path/to/your/directory"

# Find duplicates
duplicates = main()
```

### Command Line Usage

```bash
python duplicate_finder.py /path/to/search true true
```

Parameters:
- Path to search
- Match by name (true/false)
- Match by size (true/false)

## Usage Examples

### 1. Find Duplicates Only

```python
# Set your configuration
SAME_NAME = True
SAME_SIZE = True
INPUT_PATH = "/Users/username/Documents"

# Find and display duplicates
duplicates = main()
```

### 2. Preview Removal

```python
# Preview what would be deleted with different strategies
preview_removal(duplicates, 'first')          # Keep first alphabetically
preview_removal(duplicates, 'shortest_path')  # Keep shortest path
preview_removal(duplicates, 'longest_path')   # Keep longest path
```

### 3. Safe Removal with Confirmation

```python
# Remove duplicates with user confirmation
confirm_and_delete(duplicates, 'first')
```

### 4. Direct Removal (Advanced)

```python
# Remove without confirmation (use with caution)
files_deleted, files_kept, space_saved = remove_duplicates(
    duplicates, 
    keep_strategy='shortest_path', 
    dry_run=False
)
```

## Configuration Options

### Matching Criteria

- `SAME_NAME = True`: Match files by filename
- `SAME_SIZE = True`: Also match by file size
- If `SAME_SIZE = False`, only filename matching is used

### Keep Strategies

When removing duplicates, you can choose which file to keep:

- **`'first'`**: Keep the first file alphabetically
- **`'last'`**: Keep the last file alphabetically
- **`'shortest_path'`**: Keep the file with the shortest path
- **`'longest_path'`**: Keep the file with the longest path

## Jupyter Notebook Workflow

### Cell 1: Find Duplicates
```python
# Configure and find duplicates
SAME_NAME = True
SAME_SIZE = True
INPUT_PATH = "/path/to/search"

duplicates = main()
```

### Cell 2: Analyze Results
```python
# Preview different removal strategies
preview_removal(duplicates, 'shortest_path')
```

### Cell 3: Remove Duplicates
```python
# Safely remove with confirmation
confirm_and_delete(duplicates, 'shortest_path')
```

## Function Reference

### Core Functions

#### `find_duplicates(path, check_name=True, check_size=True)`
Finds duplicate files in the specified directory.

**Parameters:**
- `path` (str): Directory path to search
- `check_name` (bool): Whether to match by filename
- `check_size` (bool): Whether to match by file size

**Returns:**
- `dict`: Dictionary with duplicate groups

#### `remove_duplicates(duplicates, keep_strategy='first', dry_run=True)`
Removes duplicate files based on the specified strategy.

**Parameters:**
- `duplicates` (dict): Dictionary from `find_duplicates()`
- `keep_strategy` (str): Strategy for choosing which file to keep
- `dry_run` (bool): If True, only shows what would be deleted

**Returns:**
- `tuple`: (files_to_delete, files_kept, total_space_saved)

#### `preview_removal(duplicates, keep_strategy='first')`
Shows a preview of what files would be deleted without actually deleting them.

#### `confirm_and_delete(duplicates, keep_strategy='first')`
Shows preview and asks for user confirmation before deleting files.

## Output Example

```
Searching for duplicates in: /Users/username/Documents
Match by name: True
Match by size: True

Found 3 duplicate groups:
==================================================

Group 1: 'document.pdf' (2.1 MB)
Found 2 duplicates:
  /Users/username/Documents/document.pdf
  /Users/username/Documents/backup/document.pdf

Group 2: 'image.jpg' (1.5 MB)
Found 3 duplicates:
  /Users/username/Documents/photos/image.jpg
  /Users/username/Documents/gallery/image.jpg
  /Users/username/Documents/temp/image.jpg

Summary: 5 duplicate files in 2 groups

=== REMOVAL PREVIEW (Strategy: shortest_path) ===

Files that would be KEPT (2):
  ✓ /Users/username/Documents/document.pdf
  ✓ /Users/username/Documents/photos/image.jpg

Files that would be DELETED (3):
  ✗ /Users/username/Documents/backup/document.pdf (2.1 MB)
  ✗ /Users/username/Documents/gallery/image.jpg (1.5 MB)
  ✗ /Users/username/Documents/temp/image.jpg (1.5 MB)

Total space that would be saved: 5.1 MB
```

## Safety Features

- **Dry Run Mode**: Preview operations before execution
- **User Confirmation**: Requires explicit confirmation for deletions
- **Error Handling**: Gracefully handles file access errors
- **Detailed Logging**: Shows exactly what files are being processed
- **Space Calculation**: Shows potential space savings before deletion

## Use Cases

- **System Cleanup**: Remove duplicate downloads, documents, and media files
- **Storage Optimization**: Reclaim disk space by removing redundant files
- **File Organization**: Identify and manage duplicate content across directories
- **Backup Verification**: Find duplicate files between backup locations
- **Media Management**: Clean up photo and video collections

## Requirements

- Python 3.6 or higher
- No external dependencies required

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Sakib Ahmed Shuva**
- GitHub: [@SakibAhmedShuva](https://github.com/SakibAhmedShuva)

## Acknowledgments

- Built with Python's standard library for maximum compatibility
- Designed for both command-line and Jupyter notebook environments
- Inspired by the need for safe and flexible duplicate file management

---

⭐ If you find this tool useful, please consider giving it a star on GitHub!
