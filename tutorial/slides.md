---
author: Geoff Hing & Derek Willis
---

# Introduction to the command line

Using GitHub Codespaces

https://github.com/dwillis/command-line-umd

In particular: `tutorial/README.md`

Derek Willis <dpwillis@umd.edu>

---

## Goal

- Cover fundamental concepts
- Help avoid common pain points

---

## Topics

- Accessing the command-line with GitHub Codespaces
- Getting unstuck
- Navigating the filesystem
- Creating and modifying files
- Viewing and previewing files
- Searching for files and their contents
- Redirecting input and output

---

## What is the command-line?

- A means of interacting with a computer and its operating system
- Runs programs and manages their inputs and outputs
- Does this with lines of text

---

## Why use the command-line?

- Prerequisite for many programming/data tools and frameworks
- Helps make data work reproducible
- Easily run operations on many inputs 
- Allows working with larger data
- Gives you data signals fast
- Helps you think in smaller programatic units

---

## Accessing the command-line with GitHub Codespaces

To access the command line in GitHub Codespaces:

- Open the GitHub repository in your web browser
- Click the green `Code` button on the repository page
- Select the `Codespaces` tab
- Click `Create codespace on main`
- Wait for the codespace to load
- Open terminal: `Terminal` > `New Terminal` or `Ctrl+Shift+\``

---

## Setting up csvkit

Install csvkit, a Python tool for working with CSV data:

```bash
pip install csvkit
```

**csvkit** is a suite of command-line tools for converting to and working with CSV files. It includes utilities like:
- `in2csv` - converts Excel, JSON, and other formats to CSV
- `csvgrep` - search CSV files by column
- `csvcut` - extract specific columns
- `csvstat` - generate summary statistics

---

## Setting up slides

Install the slides presentation tool:

```bash
go install github.com/maaslalani/slides@latest
```

Then run the slides:

```bash
slides tutorial/slides.md
```

Use arrow keys to navigate through slides, `q` to quit.

---

## Using multiple terminals

In VS Code, you can open multiple terminal tabs:

- Click the `+` icon next to your terminal tab to create a new terminal
- Use `Ctrl+Shift+\`` to open a new terminal
- Click between terminal tabs to switch contexts
- **Tip**: Use one terminal for slides, another for running commands
- You can also split terminals using the split panel icon

---

## There's another layer

- Program that interprets the command is called the *shell*.
- We're using Bash, the default in GitHub Codespaces.
- There are many others: `sh`, `zsh`, `ksh`.
- Concepts and syntax are similar but will vary slightly.

---

## The command-line is case (and space) sensitive

Spaces separate arguments, so use one of these for a file with a space:

```
ls My\ Data
ls 'My Data'
ls "My Data"
```

not

```
ls My Data
```

---

## Press `return` on your keyboard to run a command

Assume you'll do this after each command, unless I explicitly say otherwise.

---

## Tutorial structure

- What we're learning
- Try it together
- Try it yourself

---

## Getting unstuck

### What we're learning

Concepts:

- `<ctrl>+c` exits the current command or gives you a new prompt.

---

## Getting unstuck 

### Try it together

#### Run a simple command

```bash
echo "hello command line"
```

---

## Getting unstuck

### Try it together

#### Exiting a running command 

```bash
echo "hello
```

Hold down the `control` key and the `c` key together to exit.

We'll write these key combinations as `<ctrl>+c`.

---

## Getting unstuck

### Try it together

#### Abandoning a command

Type this, but **don't** press `return`:

```bash
echo
```

Then press `<ctrl>+c` together.

---

## Navigating the filesystem

### What we're learning 

Commands:

- `cd`
- `pwd`
- `ls`

---

## Navigating the filesystem

### What we're learning 

Concepts:

- *Absolute* and *relative* *paths*
- *Arguments* to *commands*
- The meaning of the special paths  `~`, `.` and `..`.
- *Command* *options*
- Using filename generation and the `*` symbol.
- *Tab completion*

---

## Navigating the filesystem

### Try it together

See where we are on the filesystem, i.e. the *working directory*:

```bash
pwd
```

The output shows the *absolute path*, i.e. all the way from `/`.

---

## Navigating the filesystem

### Try it together

Change directory to the tutorial folder:

```bash
cd tutorial
```

In GitHub Codespaces, you'll start in the project root directory.

---

## Navigating the filesystem

### Try it together

List contents of current directory:

```bash
ls
```

---

## Navigating the filesystem

### Try it together

Change directory to a *relative path*:

```bash
cd tutorial
```

---

## Navigating the filesystem

### Try it together

Explore files in the VS Code file explorer (left sidebar) or use the terminal to browse:

```bash
ls .
```

You can double-click `README.md` and `solutions.md` in the file explorer to open them.

---

## Navigating the filesystem

### Try it together

Change directory to the parent (`..`):

```bash
cd ..
```

---

## Navigating the filesystem

### Try it together

List files in directories other than the current one.

Relative path:

```bash
ls tutorial
```

Subdirectory:

```bash
ls tutorial/data
```

Absolute path:

```bash
ls /
```

---

## Navigating the filesystem

### Try it together

Show details about files in the directory:

```bash
ls -l tutorial
```

---

## Navigating the filesystem

### Try it together

Combine options to show all files and sizes in human-readable form:

```bash
ls -alh tutorial
```

---

## Navigating the filesystem

### Try it together

Save typing by using the `*` wildcard:

```bash
ls tut*
```

```bash
ls tutorial/*.md
```

---

## Navigating the filesystem

### Try it together

Save typing by using *tab completion*:

```
ls tu<tab>/d<tab>/c<tab>
```

Should result in this command showing up in your shell:

```
ls tutorial/data/census-bureau-popest
```

---

## Navigating the filesystem

### Try it together

What happens when there are multiple paths that match what you've typed so far? For example:

```
ls tutorial/data/census-bureau-popest/20<tab>
```

---

## Navigating the filesystem

### Try it yourself 

- Change directory to `tutorial`
- Using `ls` or a combination of `cd` and `ls`, what is the most recent fiscal year for which ICE detention statistics are available?

---

## Navigating the filesystem

### Try it yourself 

```bash
cd tutorial
ls data
ls data/ice-detention-statistics/
```

Answer: 2025

---

## Creating and modifying files

### What we're learning

Commands:

- `mkdir`
- `touch`
- `mv`
- `cp`
- `rm`
- `rmdir`
- `history`

---

## Creating and modifying files

### What we're learning

Concepts:

- Using the arrow keys to retrieve command history.
- Using `<ctrl>+r` to search command history.

---

## Creating and modifying files

### Try it together

Make sure you're in the `tutorial` subdirectory.

Remember, you can use `pwd` to check.

---

## Creating and modifying files

### Try it together

Make a directory to hold some data:

```bash
mkdir data/manual
```

---

## Creating and modifying files

### Try it together

Create some empty text files:

```bash
touch data/manual/mok_data_1.txt
touch data/manual/mok_data_2.txt
```

---

## Creating and modifying files

### Try it together

Fix the typo by renaming the files with `mv`.

Remember to use tab completion!

```bash
mv data/manual/mok_data_1.txt data/manual/mock_data_1.txt
mv data/manual/mok_data_2.txt data/manual/mock_data_2.txt
```

---

## Creating and modifying files

### Try it together

`mv` can also move files and directories:

```bash
mkdir data/manual/mock_data
```

```bash
mv data/manual/mock_data_*.txt data/manual/mock_data
```

---

## Creating and modifying files

### Try it together

`cp` makes copies of files:

```bash
cp data/manual/mock_data/mock_data_1.txt data/manual/mock_data/mock_data_3.txt
```

---

## Creating and modifying files

### Try it together

Delete files using `rm`:

```bash
rm data/manual/mock_data/mock_data_*
```

Delete empty directories using `rmdir`:

```bash
rmdir data/manual/mock_data
```

---

## Creating and modifying files

### Try it together

If we want to review commands we've run, use

```bash
history
```

---

## Creating and modifying files

### Try it together

We can use re-run previous commands, stepping through the commands with the up and down arrow keys.

Press the up arrow key until this command is visible and then press `<return>` to run it:

```bash
mkdir data/manual/mock_data
```

---

## Creating and modifying files

### Try it together

We can also search for a past command by holdng down the `control` and `r` keys together and typing a search phrase.

Type `<ctrl>+r` and then type `to`. This should cause the following command to appear. **Don't** type `<return>` to run it:

```
touch data/manual/mok_data_2.txt
```

---

## Creating and modifying files

### Try it together

You can continue the search through the history by using `<ctrl>+r` again.

This should cause this command to appear. Again **don't** type `<return>` to run it

```
touch data/manual/mok_data_1.txt
```

Instead, edit the command so it reads:

```
touch data/manual/mock_data/mock_data_1.txt
```

Then run it.

---

## Creating and modifying files

### Try it yourself

Typing the minimal number of characters, delete the file `data/manual/mock_data/mock_data_1.txt` and delete the directory `data/manual/mock_data`. 

---

## Creating and modifying files

### Try it yourself

Type `<ctrl>+r` and then `rm `, which causes the command `rm data/manual/mock_data/mock_data_*` to appear.

Then, type `<ctrl>+r` and then `rmd`, which causes the command `rmdir data/manual/mock_data` to appear.

---

## Viewing and previewing files

### What we're learning

Commands:

- `cat`
- `head`
- `tail`
- `less`
- `wc`

---

## Viewing and previewing files

### Try it together

Make sure you're in the `tutorial` subdirectory.

Remember, you can use `pwd` to check.

---

## Viewing and previewing files

### Try it together

Look at a file contents:

```bash
cat data/umpd/umpd_incidents.csv
```

---

## Viewing and previewing files

### Try it together

Look at only the first lines:

```bash
head data/umpd/umpd_incidents.csv
```

---

## Viewing and previewing files

### Try it together

Specify the number of lines to see:

```
head -n 6 data/umpd/umpd_incidents.csv
```

---

## Viewing and previewing files

### Try it together

`tail` works similarly, showing the final lines of the file.

```
tail -n 5 data/umpd/umpd_incidents.csv
```

---

## Viewing and previewing files

### Try it together

`less` shows a file page by page:

```
less data/umpd/umpd_incidents.csv
```

---

## Viewing and previewing files

### Try it together

Once inside `less`:

- `<space>` pages through the file in a forward direction.
- `b` pages through the file in a backward direction.
- `/`, followed by a pattern, will take you to the first instance of the pattern.
- `n` will repeat the search in a forward direction.
- `N` will repeat the search backward.
- `q` quits the program.

---

## Viewing and previewing files

### Try it together

To get the number of rows in a file, use `wc`:

```
wc -l data/umpd/umpd_incidents.csv 
```

---

## Viewing and previewing files

### Try it yourself

What was the type of the first incident in the UMPD Incidents CSV file on February 1, 2025?

---

## Viewing and previewing files

### Try it yourself


Use less to view the file:

```
less data/umpd/umpd_incidents.csv
```

Then, type the `/` character to search and type `2/1` and `<return>`.

---

## Searching for files and their contents

### What we're learning

Commands:

- `find`
- `grep`
- `man`

---

## Searching for files and their contents

### Try it together

Make sure you're in the `tutorial` subdirectory.

Remember, you can use `pwd` to check.

---

## Searching for files and their contents

### Try it together

Use `find` to find files matching a pattern:

```bash
find data -name '*foia*'
```

---

## Searching for files and their contents

### Try it together

Use the `-iname` option to make the search case-insensitive:

```bash
find data -iname '*foia*'
```

---

## Searching for files and their contents

### Try it together

Use `man` to learn about all the options that are available for a command:

```
man find
```

You can use the same keystrokes to navigate as with `less`, including `q` to quit.

---

## Searching for files and their contents

### Try it yourself

How would you find only FOIA logs for 2024 that are in the CSV file format?

---

## Searching for files and their contents

### Try it yourself

```bash
find data -iname '*2024*.csv'
```

---

## Searching for files and their contents

### Try it together

Use `grep` to search the contents of files:

```bash
grep -i 'tucson' data/ice-foia-logs/*.csv
```

This shows the matching filename and line content.

---

## Searching for files and their contents

### Try it together

To only show the matching files, use the `-l` option:

```bash
grep -il 'tucson' data/ice-foia-logs/*.csv
```

---

## Searching for files and their contents

### Try it together

Use the `-r` option to recursively search a directory:

```bash
grep -ilr 'tucson' data
```

---

## Searching for files and their contents

### Try it yourself

Use a different pattern to search the FOIA log CSV files for something of interest to you. What did you find?

---

## Searching for files and their contents

### Try it yourself

I used `grep` to see if there were any FOIA requests about the 287(g) program:

```
grep -Ei '287\(?g\)?' data/ice-foia-logs/*.csv
```

---

## Redirecting input and output

### What we're learning

Commands:

- `in2csv`
- `csvgrep`
- `csvformat`

---

## Redirecting input and output

### What we're learning

We're going to learn about these concepts:

- *Standard output*
- `|` (pipe) operator to redirect the output of one program into the input of another.
- `>` operator to redirect the output of a program to a file.
- Using `-h` or `--help` to get command help.

---

## Redirecting input and output

### Try it together

Let's start with generating some output.

Use grep to find FOIA log records that might be requests from lawyers:

```bash
grep -i 'law' data/ice-foia-logs/*.csv
```

---

## Redirecting input and output

### Try it together

Pipe the output of `grep` to `less` to page through the results:

```bash
grep -i 'law' data/ice-foia-logs/*.csv | less
```

---

## Redirecting input and output

### Try it together

Pipe the output `grep` to `wc` to count the number of lines that match a pattern:

```
grep -i 'tucson' data/ice-foia-logs/*.csv | wc -l
```

---

## Redirecting input and output

### Try it together

Use `in2csv` to convert from Excel to CSV:

```bash
in2csv data/ice-foia-logs/FY2024_FOIA_AppealsLog.xlsx 
```

---

## Redirecting input and output

### Try it together

Use `>` to redirect this output to a file:

```bash
in2csv data/ice-foia-logs/FY2024_FOIA_AppealsLog.xlsx > data/ice-foia-logs/FY2024_FOIA_AppealsLog.csv
```

---

## Redirecting input and output

### Try it together

Use `csvgrep` to search for matching records in a way that is aware of columns:

```bash
csvgrep -c 'Request Description' -m "Maryland" data/ice-foia-logs/2024-09_FOIA_Log.csv
```

---

## Redirecting input and output

### Try it together

Use the `-h` option to learn about a program's syntax and functionality:

```bash
csvgrep -h
```

---

## Redirecting input and output

### Try it together

Pipe the output of `csvgrep` to `csvformat` to convert CSV to TSV:

```
csvgrep -c 'Request Description' -m "Maryland" data/ice-foia-logs/2024-09_FOIA_Log.csv | csvformat -T
```

---

## Redirecting input and output

### Try it together

Save the output to a file for sharing or downloading:

```bash
csvgrep -c 'Request Description' -m "Maryland" data/ice-foia-logs/2024-09_FOIA_Log.csv | csvformat -T > tucson_requests.tsv
```

You can then download this file using VS Code's file explorer (right-click and select "Download").

---

## Redirecting input and output

### Try it yourself

- Use `csvgrep` to find requests that match "Law" in the `Requester::Organization Name` column of `data/ice-foia-logs/2024-10_FOIA_Log.csv`.
- Use `csvcut` to display only that column.
- Save this to `data/ice-foia-logs/2024_lawyer_requests.csv`.
- Bonus points: Use `uniq` and `csvsort` to get only unique lawyer/law firm names.
- Then count the number of unique names.

---

## Redirecting input and output

### Try it yourself

Use `csvgrep` to search for "Law" in the `Requester::Organization Name` column:

```bash
csvgrep -c 'Requester::Organization Name' -m 'Law' data/ice-foia-logs/2024-10_FOIA_Log.csv
```

---

## Redirecting input and output

### Try it yourself

Then pipe that output to `csvcut` to limit the columns:

```bash
csvgrep -c 'Requester::Organization Name' -m 'Law' data/ice-foia-logs/2024-10_FOIA_Log.csv | csvcut -c 'Requester::Organization Name'
```

---

## Redirecting input and output

### Try it yourself

Redirect the output to a file with `>`:

```bash
csvgrep -c 'Requester::Organization Name' -m 'Law' data/ice-foia-logs/2024-10_FOIA_Log.csv | csvcut -c 'Requester::Organization Name' > data/ice-foia-logs/2024_lawyer_requests.csv 
```

---

## Redirecting input and output

### Try it yourself

Use `csvsort` to sort the organization names so that `uniq` will deduplicate them, then count the rows with `wc -l`:

```bash
csvgrep -c 'Requester::Organization Name' -m 'Law' data/ice-foia-logs/2024-10_FOIA_Log.csv | csvcut -c 'Requester::Organization Name' | csvsort | uniq | wc -l
```
