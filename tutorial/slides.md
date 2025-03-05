---
author: Geoff Hing
---

# Introduction to the command line

NICAR 2025

https://github.com/ghing/nicar-2025-command-line

In particular: `tutorial/README.md`

Geoff Hing <ghing@themarshallproject.org>

---

## Goal

- Cover fundamental concepts
- Help avoid common pain points

---

## Topics

- Accessing the command-line on a Mac
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

## Accessing the command-line on a Mac

Using Finder:

- Open Finder.
- `Applications` > `Utilities` > `Terminal`

Using Spotlight:

- Open Spotlight search (`<cmd>+<space>` or the 🔎 icon in the menu bar).
- Start typing `terminal`.
- Click entry in search results.

---

## There's another layer

- Program that interprets the command is called the *shell*.
- We're using Z shell (Zsh), the default on Macs.
- There are many others: `sh`, `bash`, `ksh`.
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
- `open`

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

Change directory to the folder containing all the fies for this session: 

```bash
cd ~/Desktop/hands_on_classes/20250306-thursday-introduction-to-the-command-line-macs/
```

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

Open the current directory (`.`) in Finder:

```bash
open .
```

You might want to double-click `README.md` and `solutions.md`.

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

---

## Creating and modifying files

### Try it together

Make sure you're in the tutorial subdirectory.

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
