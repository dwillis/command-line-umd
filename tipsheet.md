# Introduction to the command line tip sheet

## What is the command-line interface (CLI)?

The command-line interface is a means of interacting with a computer and its operating system by running programs and managing their inputs and outputs with lines of text.

This is in contrast to a graphical user interface (GUI) where you use a device such as a touchpad or mouse to interact with visual elements such as icons, buttons and menus to launch and control programs.

## Why use the command-line?

- Prerequisite for many programming/data tools and frameworks
  - More people will use the original command-line versions of tools, so easier to get help, translate online resources than using a graphical wrapper
- Helps make data work reproducible
  - Faster to copy and paste a command you ran into your data diary than to try to explain what you clicked on in a graphical program
  - Can combine multiple commands into a script to allow someone to reproduce data processing all at once
- Easily run operations on many inputs 
- Allows working with larger data
  - Often you just want to process or analyze data, not view the whole thing. Command-line tools will often use fewer system resources to do this.
- Gives you data signals fast
  - If you just need a ballpark answer for questions like "how many rows?", "how many rows in this category?" or "does this data set include records for this city?", command-line tools will tell you this quickly. 
- Helps you think in smaller programatic units

## Command-line programs are very influenced by "the Unix Philosophy"

Most command-line programs follow ["the Unix Philosophy"](https://cscie2x.dce.harvard.edu/hw/ch01s06.html). Unix is a family of operating systems developed as early as the late 1960s, whose design is present in modern operating systems like Linux and Mac OS.

This is how one of the developers who created the operating system summarized this philosophy:

> This is the Unix philosophy: Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface.

Unix, and its successors, were very much designed as an operating system by and for programmers.

Keep these in mind when thinking about why the command-line works the way it does.

## Accessing the command-line on a Mac

We'll access the command-line through a program that is pre-installed on all Mac computers called `Terminal`. This is an example of a software called a terminal emulator, so called because it mimics early interfaces to systems that only had a monitor showing a command-line interface and a keyboard.

Using Finder (the program that you use to browse files and folders on a Mac):

- Open Finder.
- Click on the `Applications` item in the sidebar.
- Double click on the icon for the `Utilities` folder.
- Double click on the icon for `Terminal`.

Using Spotlight (the little magnifying glass icon in the bar at the upper-right-hand corner of your screen):

- Open Spotlight search by clicking on the magnifying glass icon, or holding down the `Cmd+Space` keys on your keyboard.
- Start typing `terminal` in the text input that appears.
- When you see an entry for `Terminal` appear in the search results, click on that entry, or press the `Return` key.

While `Terminal` comes with all Mac computers, many prefer to use a terminal emulator program that offers more features and customization, such as [iTerm2](https://iterm2.com/).

Many editors, such as Visual Studio Code, provide some kind of integrated terminal program.

### There's another layer

The program that is actually running in the terminal emulator to interpret the commands you enter is called a "shell".

The one we'll be using is Z shell (Zsh), which is the default on recent Mac computers. Another popular shell is Bourne Again SHell (Bash). Each shell has some syntactic differences, particularly when you're writing scripts that tie multiple commands together. However, when running most commands and using core functionality like redirecting input and output, the differences are negligible.

If you're not sure what shell you're using, you can run:

```
echo $SHELL
```

and it will output the *absolute path* of the shell program being used. When I run this command on my system, it shows `/bin/zsh`, which is the Z shell.

## The command-line is case (and space) sensitive

You need to escape spaces be either using quotation marks or a backslash (`\`).

For example, if you have a folder named `My Data`, and you wanted to list its contents, you would need to type either:

```
ls My\ Data
```

or

```
ls 'My Data'
```

or

```
ls "My Data"
```

On the command-line, single and double quotes have somewhat different behaviors, but for the purpose of handling spaces, you can use either. Just make sure they match.

Spacing is important with command options too. `uniq -c` is different than `uniq - c`. If you're getting strange errors, make sure that you're tying the command correctly and don't have spaces between the hyphen and letter in options.

## Starting over: Use `ctrl+c`

If you want to abandon a command you've started typing and get a new command prompt, you can hold down the `ctrl` and `c` keys at the same time (this is written as `ctrl+c`) and you will be given a new command prompt.

Similarly, if you run a command and it gets into an unexpected state, or is running longer than you expect, you can use `ctrl-c` to exit the program and return you to a new prompt.

### Anatomy of a command

Most commands follow this format.

`command [options] [positional_arguments ...]`

Example: `ls -al ~`

- `ls`: program 
- `-al`: options
- `~`: positional argument

Many commands have both short and long versions of options. For example, these commands are equivalent:

```
csvgrep -c 'Requester::Organization Name' -m 'Law' data/ice-foia-logs/2024-08_FOIA_Log.csv 
```

```
csvgrep --columns 'Requester::Organization Name' --match 'Law' data/ice-foia-logs/2024-08_FOIA_Log.csv 
```

The short, single-character options are good for typing quickly and the long options are better for use in a script or data diary, where you want the reader to have a better idea of what a command is doing without consulting documentation.

## Getting help

Most command-line programs have some kind of built-in documentation on your system.

To find out all options, you can often, but not always, use the `-h` option for a command. For example:

```
csvgrep -h
```

For a more verbose set of instructions, you can view the command's manual page, with the `man` command.

For example,

```
man ls
```

will show you the manual page for the `ls` command.

To browse the manual page, you can use space to page down, arrow keys to go up/down line-by-line, and `q` to quit.

I often like to use `/` to search for the "EXAMPLES" section that is present in many manual pages, which I often find most helpful for quickly understanding how to use a program.

## Editing and reusing commands

### Arrow keys let you step through previous comands one-by-one

### `history` shows you a big chunk of history

### `ctrl+r` lets you search your history

### Navigating the current command

- `ctrl-a`: Move cursor to the beginning of the line
- `ctrl-e`: Move cursor to the end of the line
- `esc-f`: Move cursor forward one word
- `esc-b`: Move cursor back one word

Again, there's a lot more.

## Navigating the file system

### Absolute and relative paths

You can think of the filesystem on a Unix system as a tree or hierarchy, it starts at the root, which is denoted by the `/` symbol. Each level below the root is separated with another `/` symbol.

For example, on my system, this file lives at `/Users/ghing/workspace/nicar-2025-command-line/tipsheet.md`, 4 levels below the root.

On the command-line, the string that tells the program where to find a file or directory is called a *path*.

When a *path* is referenced beginning with a `/`, it is called an *absolute* path. The path contains all of the file or directories *parents* all the way down from the root.

When a *path* doesn't begin with a `/`, it's a *relative path*. That is, it's relative to your current working directory.

If I'm currently in the directory `/Users/ghing/workspace/nicar-2025-command-line`, I could reference `tutorial/solutions.md` like that - using its relative path. I could also reference it with the absolute path, `/Users/ghing/workspace/nicar-2025-command-line/tutorial/solutions.md`.

### Some special paths 

- `.`: The current directory
- `..`: The parent directory
- `~`: The home directory. The files you create and own, as well as system configuration for your user, live somewhere under this directory. On a Mac, this is a subdirectory of `/Users`

### `pwd` tells you where you are

Running

```
pwd
```

will print the *absolute path* of the current working directory.

Use this if you're confused about where you are on the filesystem.

### `cd` changes directory

To move around the filesystem, use `cd`.

If I'm in this project directory, I can use

```
cd tutorial
```

to change the working directory to the `tutorial` subdirectory.

To move back up, I can use:

```
cd ..
```

If I wanted to go up two levels, I would use:

```
cd ../..
```

Without any arguments, `cd` will change directory to a user's home directory. It's equivalent to `cd ~`.

### `ls` lists directory contents and file details

Without any arguments, `ls` will show you the contents of the current directory.

You can also specify a path and ls will show you the contents of that directory:

```
ls tutorial
```

Or, you can specify an absolute path:

```
ls /opt/homebrew
```

Using the `-l` option will show more details of an individual file:

```
ls -l tutorial/solutions.md
```

or a all the files in a directory:

```
ls -l tutorial
```

The details include the permissions, the user and group ownership, the size and modification timestamp.

The `-h` option causes file sizes to be shown with human-readable units:

```
ls -lh tutorial
```

will show a file's size as `22K` instead of `22517`.

## Filename generation

Typing out the full path to multiple files can be tedious. Luckily, there are patterns that can be used to match multiple paths.

- `*`: Matches any string
- `?`: Matches any single character
- `(x|y)`: Matches `x` or `y`
- `<[x]-[y]>`: Matches any number in the range x to y, inclusive.

There's a lot more. See the [Expansion](https://zsh.sourceforge.io/Doc/Release/Expansion.html#Filename-Expansion) section of the Zsh manual.

For example, instead of typing:

```
ls -lh tutorial/data/ice-foia-logs/2024-08_FOIA_Log.csv tutorial/data/ice-foia-logs/2024-09_FOIA_Log.csv tutorial/data/ice-foia-logs/2024-10_FOIA_Log.csv
```

I could just type:

```
ls -lh tutorial/data/ice-foia-logs/2024*_FOIA_Log.csv
```

By convention, files and directories that begin with `.`, e.g. `~/.zshrc` are *hidden*. To show hidden files, use the `-a` option, e.g.:

```
ls -a ~
```

## `<tab>` auto-completes programs, paths and more 

Another way to avoid typing is to use tab completion.

If you start typing a command or a file path, and then press the `tab` key, the shell will complete the matching command or path. If there are multiple matches for what you've typed so far, the shell will show you the potential matches.

For example, if I type

```
ls tu<tab>
```

The shell will expand that to

```
ls tutorial/
```

If I type

```
ls t<tab>
```

this could match two files or directories and the shell will show me the options: `tipsheet.md` and `tutorial`.


## Creating and modifying files

### `mkdir` creates directories

The simple version creates a new, empty directory in the current working directory:

```
mkdir source_data
```

You can also specify the parent, and the directory will be created there:

```
mkdir data/source/arrests
```

The above command creates `arrests` in the `data/source` directory.

It assumes the parent directories `data` and `source` exist.

But, if you want to create a new directory, and all its parents, use the `-p` option:

```
mkdir -p data/source/arrests
```

### `touch` creates empty files

It also updates the timestamp of existing files.

### `mv` renames files and moves them to different directories

To rename a file, make the second argument the new name, e.g.

```
mv mok_data.csv mock_data.csv
```

This works with directories too:

```
mv src_data source_data
```

If the second argument is a directory that exists, the file will be moved there instead of renamed:

```
mv mock_data.csv data/source
```

You can move multiple files to a directory, or use wildcards:

```
mv mock_data_1.csv ~/Downloads/mock_data_2.csv data/source
```

```
mv mock_data*.csv data/source
```

### Renaming multiple files, matching a pattern

Zsh has a built-in command called `zmv`, which allows you to rename files, capturing the part of the filename that matches a wildcard pattern in the first argument and making it available to the second argument, the format of the renamed files.

To make `zmv` available to the shell, first run:

```
autoload zmv
```

Then you can run a command like this: 

```
zmv 'data/source/national_caseload__annual__202302__disk(*)' 'data/source/national_caseload__monthly__202302__disk$1'
```

The above examole changes the file prefix by inserting "monthly" but preserves the disk numbers.

See [How to use zmv — Z Shell’s super-smart file renamer](https://blog.smittytone.net/2021/04/03/how-to-use-zmv-z-shell-super-smart-file-renamer/) for more examples.

If you're using a different shell, you could install [rename](http://plasmasturm.org/code/rename/).

### `rm` deletes files

Many people alias `rm` to `rm -i` so it asks you for confirmation before deleting a file.

### `rmdir` deletes empty directories

If this command fails, check that there aren't hidden files, with `ls -a`.

To delete a directory that contains files, as well as all the files in that directory and its descendents, use the `-r` (recurse) and `-f` options.

⚠️ Be extremely careful with this command. It will not ask you to confirm, and you can't recover the files.

```
rm -rf tutorial/data/manual
```

## Viewing and previewing files

`cat` will show the contents of a text file. `cat` is short for concatenate, and can be used to combine text files, but when only one file is given as an argument, it just shows the contents.

`head` will show you the beginning of a file.

`tail` will show you the end of a file.

`less` will show you the contents of a text file one "page" at a time.

Within `less`, pressing the space bar will go to the next "page" of text. Pressing `b` will show you the previous.

Typing `/` followed by a pattern, will take you to the first instance matching the pattern in the forward direction. Then, `n` will repeat that search. `N` will repeat that search in the backward direction. 

## Searching files

### `find` searches file names/metadata

If we want to see if any file or directory **names** match a pattern, use `find`.

`find`'s syntax is a bit different than many commands in terms of the position of the arguments and options, and the format of the options.

Let's look at an example, that finds all files or directories with "foia" (or "FOIA") in the name:

```
find tutorial/data -iname '*foia*' -not -type d
```

- `find`: The name of the program.
- `tutorial/data`: Find files that live under this directory.
- `-iname '*foia*'`: Only find files with 'foia' somewhere in the name. We quote this because we want the pattern to be handled by `find`, not expanded by the shell, which causes an error.
- `-not -type d`: Don't return directories.

### `grep` searches contexts of text files

If we want to search the **contents** of text files, use `grep`.

## Redirecting input and output

The output of a program is sent to *standard output* (often abbreviated as stdout). The default input of a program is called *standard input*.

'>' redirects the output of a command to a file.

'>>' appends the output of a command to a file.

'<' cause the contents of a file to be read as a command's input.

'|' between commands redirects the output of one command into the input of the next. This feature is what enables the "Unix philosophy" of writing small, single-purpose programs.

There's also *standard error*. If you still see terminal output after redirecting *standard output*, the remaining output is probably being written to *standard error*. You can redirect that separately. See the [Zsh redirection documentation](https://zsh.sourceforge.io/Doc/Release/Redirection.html) for a complete list.

## Running commands on many inputs

### `find` can run a command for each matching file

The `find` command has an `-exec` option that will run a command on all files matched by `find`.

This is the command I used to create the CSV versions of the Excel spreadsheets of 2024 ICE FOIA logs:

```
find tutorial/data/ice-foia-logs -name '2024*' -exec sh -c 'in2csv "{}" > tutorial/data/ice-foia-logs/$(basename "{}" | sed s/xlsx/csv/)' \;
```

Let's break this down:

- `find`: The name of the program we're running.
- `tutorial/data/ice-foia-logs`: Search for all files under this directory.
- `-name '2024*'`: Only find files that begin with "2024".
- `-exec`: For each file found, run a command ...
- `sh`: This is the command that is run for each file. It is another shell. In many uses of `find -exec`, we don't need to use this, but we need to do some more complex things in the command.
- `-c`: In the shell, `sh`, run the command specified in the string.
- `in2csv "{}" > tutorial/data/ice-foia-logs/$(basename "{}" | sed s/xlsx/csv/)`: This is the command run in the shell.
  - `in2csv`: Run the `in2csv` program ...
  - `"{}"`:  ... on this file. `{}` will be replaced by the path of the file discovered by `find`.
  - `>`: redirect the output of `in2csv` to a file.
  - `tutorial/data/ice-foia-logs/`: the output file should live under this directory
  - `$(basename "{}" | sed s/xlsx/csv/)`: the name of the file. We get the filename by running another set of commands.
    - `$()`: Runs the part inside the parens as a command
    - `basename "{}"`: Get the file portion only of the file. `{}` will be replaced by the path of the file discovered by `find`.
    - `|`: pass the output of `basename` to the input of another program.
    `sed s/xlsx/csv/`: That other program is `sed`. Provide an expression that substitutes `xlsx` in the input string (in this case, the filename) with `csv`.
- `\;`: Tell `find -exec` this is the end of the command.

That's an inception level of complexity. I often build commands like this by trying out each portion separately.

For example, I'll run

```
echo 'foo.xlsx' | sed s/xlsx/csv/
```

then

```
basename tutorial/data/ice-foia-logs/FY2024_FOIA_AppealsLog.xlsx | sed s/xlsx/csv/
FY2024_FOIA_AppealsLog.csv
```

then a simpler version of `find -exec`, like:

```
find tutorial/data/ice-foia-logs -name '2024*' -exec echo "{}" \;
```

until I understand how each piece works. Then I combine it all together.

### `xargs` runs a command for a list of items

The `xargs` command takes a list of items on standard input and runs a command on them. 

For example, to use `curl` to download all the URLs in a text file, use:

```
xargs -n 1 curl -O < ice_detention_statistic_urls.txt
```

Let's disect this command:

- `xargs`: The program we're running.
- `-n 1`: Read one argument from standard input. This is because there is only one item per line in the input file, the URL to download.
- `curl -O`: The command that will be run for each line of standard input.
  - `curl`: The program that will be run. `curl` is a command-line tool to make network requests, particularly HTTP.
  - `-O`: Option that tells curl to save the downloaded file using the filename portion of the URL.
- `< ice_detention_statistic_urls.txt`: Instead of reading the input from standard input, `xargs` should read its input from the file `ice_detention_statistic_urls.txt`.

One note about `curl`! Many browser developer tools' network panel let you copy a request as a curl command! This is great for replaying and modifying network requests.

## Next steps

There are so many other topics that are beyond the scope of an introduction, but that I use regularly in my work. Here are some other concepts that you might want to check out, in no particular order.

- How the shell finds programs and decides which one to run, i.e. the *system path*.
- File permissions
- Environment variables
- Shell expansion
- Customizing your environment
  - Customizing your prompt
  - Aliases
- Suspending and killing processes and running longrunning processes in parallel
- Exit codes, using them to run commands conditionally with `&&` and `||`
- Installing command-line software
- Using the command-line on remote systems
- Regular expressions
- Processing text with `awk` and `sed`

## Resources

### Past NICAR tipsheets

- [AJVicens/command-line-for-reporters](https://github.com/AJVicens/command-line-for-reporters): Tip sheet from this session at a past NICAR conference. 
- [armendariz/terminal_recipes](https://github.com/armendariz/terminal_recipes): Tip sheet for a similar session from the 2015 NICAR conference.
- [chrislkeller/nicar15-command-line-basics](https://github.com/chrislkeller/nicar15-command-line-basics): Tip sheet from a different version of the 2015 NICAR conference.
- [useful tools for the command line](https://docs.google.com/presentation/d/1TwQdzwfjrAaNxbVlkRa_2zn6UPOFFOkOcFOTb0mASTw/edit#slide=id.ga856f3037_028)
- [KarrieK/NICAR16](https://github.com/KarrieK/NICAR16): Tip sheet and tutorial for a similar session at the 2016 NICAR conference. This one is more focused on csvkit.

### General command line references

- [Command line crash course - Learn web development](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Environment_setup/Command_line) (Mozilla Developers Network): A good general tutorial, similar in scope to this one.
- [veltman/clmystery: A command-line murder mystery](https://github.com/veltman/clmystery): A really fun murder mystery activity for practicing using the command line.
- [You Suck at Programming](https://ysap.sh/): Entertaining videos about shell scripting and using Unix tools.

### Redirecting input and output

- [Input/Output Redirection in the Shell](https://thoughtbot.com/blog/input-output-redirection-in-the-shell)

### Tools

- [simonw/llm-cmd](https://github.com/simonw/llm-cmd): A plugin to Simon Willison's [LLM](https://llm.datasette.io/en/stable/) command-line utility that suggests commands based on human-language descriptions of the task.
