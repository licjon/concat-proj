# concat_proj

A utility tool designed to help developers provide code context to AI chat assistants (like ChatGPT, Claude, etc.) by combining multiple project files into a single, well-formatted text file.

## Purpose

When seeking help with coding questions, providing proper context about your codebase is crucial for getting accurate assistance. However, copying and pasting multiple files or explaining complex directory structures can be tedious and error-prone. `concat_proj` solves this by:

- Automatically combining multiple files from your project into a single file
- Preserving directory structure information
- Making it easy to share your code context with AI assistants

## Installation

1. Download `concat_proj.py` to your local machine
2. Ensure you have Python 3.6 or higher installed
3. No additional dependencies required!

You can use the script in two ways:

### Option 1: From Project Directory
1. Copy `concat_proj.py` to your project directory
2. Run:
```bash
python concat_proj.py
```

### Option 2: From Any Location (Recommended)
1. Keep `concat_proj.py` in a convenient location (e.g., your tools or scripts directory)
2. Use the `--root` option to specify your project path:
```bash
# Windows example
python C:/Users/YourName/Tools/concat_proj.py --root C:/Projects/MyProject

# Unix/Mac example
python ~/tools/concat_proj.py --root ~/projects/my_project
```

Pro Tip: You can create an alias or add the script to your PATH for easier access:
```bash
# Unix/Mac alias example (add to .bashrc or .zshrc)
alias concat_proj='python ~/tools/concat_proj.py'

# Then use it like this:
concat_proj --root ~/projects/my_project
```

## Examples for Different Locations

```bash
# Script is in current directory, project is elsewhere
python concat_proj.py --root ../other_project

# Script is in tools directory, analyzing current directory
python ~/tools/concat_proj.py --root .

# Script is in tools directory, analyzing specific project
python ~/tools/concat_proj.py --root ~/projects/my_project

# Include specific files from a different project
python ~/tools/concat_proj.py --root ~/projects/my_project --include "**.py" "**.java"

# Specify output location in a different directory
python ~/tools/concat_proj.py --root ~/projects/my_project --output ~/Desktop/context.txt
```

## Advanced Usage

### Include Specific File Types
```bash
# Only Python files
python concat_proj.py --include "**.py"

# Python and Java files
python concat_proj.py --include "**.py" "**.java"

# Files in specific directory
python concat_proj.py --include "**/models/**.py"
```

### Change Output Location
```bash
python concat_proj.py --output my_context.txt
```

### See All File Types in Your Project
```bash
python concat_proj.py --list-extensions
```

### Additional Options
```bash
# Exclude directory structure visualization
python concat_proj.py --no-structure

# Add custom ignore patterns
python concat_proj.py --ignore "**/tests/*" "**/*.log"

# Specify different project directory
python concat_proj.py --root /path/to/project
```

## Tips for Using with AI Chat

1. **Be Selective**: Only include relevant files to your question. Use the `--include` option to select specific files or directories.
   ```bash
   python concat_proj.py --include "**/relevant_module/**.py"
   ```

2. **Provide Context**: When pasting into AI chat, start with a clear description of your question or issue, then mention you're providing code context.
   Example:
   ```
   I'm having trouble with the authentication system in my Flask application. 
   Here's my current code structure and implementation:
   [paste concat_proj output here]
   ```

3. **Check File Size**: If the combined output is very large, consider using `--include` to focus on the most relevant files for your question.

4. **Formatting**: The output is already formatted to be readable in AI chat interfaces. Each file is clearly marked with separators and its path in the project.

## Common Use Cases

1. **Debugging Complex Issues**:
   ```bash
   python concat_proj.py --include "**/relevant_module/**.py" "**/tests/test_relevant.py"
   ```

2. **Architecture Questions**:
   ```bash
   python concat_proj.py --include "**.py"  # Include all Python files to show project structure
   ```

3. **Specific Feature Implementation**:
   ```bash
   python concat_proj.py --include "**/feature_name/**"
   ```

## What Gets Ignored

By default, the tool ignores:
- Hidden files and directories (starting with .)
- Build directories (dist, build, target, etc.)
- Compiled files (.pyc, .class, .o, etc.)
- Package management directories (node_modules, __pycache__, etc.)
- Binary and compressed files (.exe, .dll, .zip, etc.)
- Most virtual environment folders (can be named anything, so ignores common naming patterns)

## Contributing

Feel free to submit issues and enhancement requests!

## License

This project is open source and available under the MIT License.
