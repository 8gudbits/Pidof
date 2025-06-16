# Pidof

Pidof is a lightweight command-line utility for retrieving process IDs (PIDs) based on image names or window titles. It provides a simple way to list running processes along with their PIDs and memory usage.

## Usage

```bash
pidof [<filename>...[--title/-t <title>]] [--help/-h] [--nobanner/-n]
```

## Options

- `-h, --help` → Display the help menu.
- `-n, --nobanner` → Suppress the banner.
- `-t, --title` → Search for processes by window title instead of filename.
- `<filename>` → Specify the process filename(s) to find the PID.

## Example Commands

```bash
pidof notepad.exe
pidof --title "Untitled - Notepad"
pidof notepad.exe --nobanner
```

## Download exe for Windows

This tool is part of the [8gudbitsKit](https://github.com/8gudbits/8gudbitsKit) project. To download the executable for Windows, visit the [8gudbitsKit](https://github.com/8gudbits/8gudbitsKit) repository.

## For the Tech People

### **1. Process Lookup via `tasklist`**

- Uses Windows built-in `tasklist` command to fetch process details.
- Filters results based on either **image name** (`IMAGENAME eq <filename>`) or **window title** (`WINDOWTITLE eq <title>`).
- Executes the command using `_popen()` to capture output dynamically.

### **2. Parsing & Data Extraction**

- The output from `tasklist` is in CSV format, which is split into lines using a custom `split()` function.
- Each line is further broken into columns, extracting **PID**, **memory usage**, and **image name**.
- The `trimQuotes()` function removes unnecessary quotes from CSV fields for clean output.

### **3. Output Formatting**

- Uses `std::setw()` to align columns properly for readability.
- Displays **PID first**, followed by **memory usage**, then **image name**.
- Ensures a structured table-like format for easy scanning.

### **4. Command-Line Argument Handling**

- Supports multiple filenames and titles via command-line arguments.
- Flags like `--title`, `--nobanner`, and `--help` are processed dynamically.

### **5. Banner & Help System**

- Displays a banner unless suppressed with `--nobanner`.
- Provides a structured help menu when `--help` is invoked.

This ensures efficient process lookup while maintaining a clean and readable output format.
