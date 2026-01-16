# Linux Command Execution and Streams

## Standard Streams

When you execute a command in Linux, it interacts with three default streams:

- **stdin (standard input)** - File descriptor: 0
    - Receives input data (typically from keyboard or another command)
- **stdout (standard output)** - File descriptor: 1
    - Sends normal output (typically to terminal)
- **stderr (standard error)** - File descriptor: 2
    - Sends error messages (typically to terminal)

These streams transfer data as simple text and can be redirected to files, other commands, or discarded.

## Redirection

### Output Redirection

- `command > file.txt` - Redirects stdout to file (overwrites)
- `command >> file.txt` - Redirects stdout to file (appends)
- `command 2> error.txt` - Redirects stderr to file (overwrites)
- `command 2>> error.txt` - Redirects stderr to file (appends)

### Combined Redirection

- `command > output.txt 2>&1` - Redirects both stdout and stderr to same file
- `command &> output.txt` - Shorthand for redirecting both streams (Bash 4+)
- `command > output.txt 2> error.txt` - Redirects stdout and stderr to different files

### Discarding Output

- `command > /dev/null` - Discards stdout
- `command 2> /dev/null` - Discards stderr (suppresses errors)
- `command &> /dev/null` - Discards both stdout and stderr

**Example:**

```bash
ls > output.txt           # Save file list to output.txt
lg 2> /dev/null          # Run 'lg' and suppress error messages
```

## Pipes

The pipe operator `|` takes stdout from one command and feeds it as stdin to the next command, enabling command chaining.

**Examples:**

```bash
ls -la /etc | less                    # View long directory listing page by page
cat file.txt | grep "error" | wc -l  # Count lines containing "error"
ps aux | grep python                 # Find running Python processes
```

## Viewing File Content

### less

Opens files in a paginated viewer without cluttering your terminal. Useful for large files.

**Usage:**

```bash
less /var/log/syslog      # View system log
ls -la /etc | less        # Pipe output to less
```

**Navigation:**

- `q` - Quit
- `Space` or `f` - Forward one page
- `b` - Backward one page
- `/pattern` - Search forward
- `?pattern` - Search backward
- `n` - Next search result
- `N` - Previous search result

### head

Displays the first lines of a file (default: 10 lines).

**Examples:**

```bash
head output.txt           # First 10 lines
head -n 15 output.txt     # First 15 lines
head -n 5 file.txt        # First 5 lines
```

### tail

Displays the last lines of a file (default: 10 lines).

**Examples:**

```bash
tail output.txt           # Last 10 lines
tail -n 15 output.txt     # Last 15 lines
tail -f /var/log/syslog   # Follow file in real-time (useful for logs)
```

## Text Processing Commands

### sort

Sorts lines of text alphabetically or numerically.

**Examples:**

```bash
sort testing.txt          # Alphabetical sort
sort -r testing.txt       # Reverse sort
sort -n numbers.txt       # Numerical sort
sort -u testing.txt       # Sort and remove duplicates
```

### tr (translate)

Translates or deletes characters.

**Examples:**

```bash
cat testing.txt | tr a-z A-Z        # Lowercase to uppercase
cat testing.txt | tr A-Z a-z        # Uppercase to lowercase
echo "hello" | tr 'l' 'L'           # Replace specific character
echo "hello world" | tr -d ' '      # Delete spaces
```

### uniq

Filters adjacent duplicate lines (works only on sorted data).

**Examples:**

```bash
uniq testing.txt                    # Remove adjacent duplicates
uniq -c testing.txt                 # Count occurrences
sort testing.txt | uniq             # Remove all duplicates (sort first)
sort testing.txt | uniq -d          # Show only duplicate lines
```

**Important:** `uniq` only removes adjacent duplicates. Always use `sort` before `uniq` to remove all duplicates.

### wc (word count)

Counts lines, words, and bytes/characters in a file.

**Examples:**

```bash
wc testing.txt            # Shows: lines words bytes filename
wc -l testing.txt         # Count lines only
wc -w testing.txt         # Count words only
wc -c testing.txt         # Count bytes only
```

### grep

Searches for patterns in text using regular expressions.

**Examples:**

```bash
grep "error" logfile.txt              # Find lines containing "error"
grep -i "error" logfile.txt           # Case-insensitive search
grep -n "error" logfile.txt           # Show line numbers
grep -v "error" logfile.txt           # Invert match (exclude lines)
grep -r "pattern" /path/to/directory  # Recursive search in directory
env | grep PWD                        # Search environment variables
ps aux | grep python                  # Find processes
```

**Common options:**

- `-i` - Ignore case
- `-n` - Show line numbers
- `-v` - Invert match
- `-r` or `-R` - Recursive search
- `-c` - Count matching lines
- `-l` - Show only filenames with matches
- `-E` - Extended regex (or use `egrep`)

## Environment Variables

Environment variables store configuration information that shells and processes use.

### Viewing Environment Variables

```bash
env                       # List all environment variables
echo $VARIABLE_NAME       # Display specific variable
env | grep PATH           # Search for specific variable
```

### Common Environment Variables

- **PWD** - Current working directory
    
    - Updates automatically when you change directories with `cd`
    - Access with: `echo $PWD` or use `pwd` command
- **PATH** - Search path for executable commands
    
    - Contains colon-separated directories
    - When you type a command, the system searches these directories in order
    - View with: `echo $PATH`
- **HOME** - User's home directory
    
- **USER** - Current username
    
- **SHELL** - Current shell being used
    

### Setting Environment Variables

```bash
export MY_VAR="value"     # Set for current session
echo $MY_VAR              # Access the variable
```

**Note:** In Linux, commands are executable files stored in directories listed in the PATH variable (like `/usr/bin`, `/bin`, `/usr/local/bin`).

## Additional Useful Commands

### cut

Extracts sections from lines of files.

**Examples:**

```bash
cut -d':' -f1 /etc/passwd           # Extract first field (usernames)
cut -c1-5 file.txt                  # Extract characters 1-5
```

### awk

Pattern scanning and processing language.

**Examples:**

```bash
awk '{print $1}' file.txt           # Print first column
awk -F':' '{print $1}' /etc/passwd  # Use custom delimiter
```

### sed

Stream editor for text transformation.

**Examples:**

```bash
sed 's/old/new/' file.txt           # Replace first occurrence per line
sed 's/old/new/g' file.txt          # Replace all occurrences
sed '1d' file.txt                   # Delete first line
```

## Command Chaining Examples

```bash
# Find top 10 largest files in current directory
ls -lh | sort -k5 -hr | head -n 10

# Count unique IP addresses in access log
cat access.log | awk '{print $1}' | sort | uniq | wc -l

# Find and count error messages
grep -i "error" /var/log/syslog | wc -l

# Display sorted, unique, lowercase words
cat file.txt | tr A-Z a-z | tr -s ' ' '\n' | sort | uniq
```

## Tips and Best Practices

1. **Always sort before using uniq** to catch all duplicates
2. **Use `less` for large files** instead of `cat` to avoid terminal clutter
3. **Redirect stderr to `/dev/null`** when you want to suppress error messages
4. **Combine commands with pipes** to create powerful one-liners
5. **Use `man command`** to read detailed documentation for any command
6. **Test redirection carefully** - `>` overwrites files without warning
7. **Use `tail -f`** to monitor log files in real-time

---
