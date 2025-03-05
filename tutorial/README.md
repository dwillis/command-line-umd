# Introduction to the command line tutorial

## Accessing the command-line on a Mac

## What we're learning

We'll learn about this concept:

- How to access the command line with software that is pre-installed on Mac computers.

## Try it together

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

## Getting unstuck

### What we're learning

We'll learn about these concepts:

- Using `<ctrl>+c` to exit a command and get a new command prompt
- Quotes in commands

### Try it together

Let's run a simple command that just outputs the string you specify. Type this command at the command prompt and press the `return` key to run it. In the future, assume that you should just press `return` after each command unless explicitly told not to.

```
echo "hello command line"
```

That's not very exciting, but it reminds us that on the command line, spaces separate *arguments* and *options* (we'll talk more about that later), so if you need to include spaces in a command's *arguments*, including ones that are file names, you need to *escape* them or wrap them in quotes. And you need to make sure to close the quotes!

What happens if we forget to close the quotes. Run this command:

```
echo "hello
```

We're in a weird state that kind of looks like the command prompt, but is a bit different. What do we do?

We can hold down the `control` key and the `c` key together, often written as `<ctrl>+c` or `^c` to kill the current program and give us a new command prompt.

We can also use `<ctrl>+c` to abandon a command we've started typing and get a new prompt.

Start typing a command, but don't press the `return` key on your keyboard.

```
echo
```

Use `<ctrl>+c` to abandon this command and get a new prompt.


## Navigating the filesystem

### What we're learning 

We're going to use these commands to move across the filesystem or learn where we are:

- `cd` changes directory to a different directory on your filesystem.
- `pwd` prints the current working directory.
- `ls` list files in the current working directory or a specified path.
- `open` opens a file or directory in the default program for that file type on your Mac.

We'll also learn about these concepts:

- *Absolute* and *relative* *paths*
- *Arguments* to *commands*
- The meaning of the special paths `~`, `.` and `..`.
- *Command* *options*
- Using filename generation and the `*` symbol.
- *Tab completion*

### Try it together

Check what directory you're in by running:

```
pwd
```

Change directory to the project root directory. At NICAR 2025, on the lab computers, this will be `~/Desktop/hands_on_classes/20250306-thursday-introduction-to-the-command-line-macs`. On my computer, the project root is instead located at `/Users/ghing/workspace/nicar-2025-command-line`.

```
cd ~/Desktop/hands_on_classes/20250306-thursday-introduction-to-the-command-line-macs
```

In this case `cd` is the *command* and `~/Desktop/hands_on_classes/20250306-thursday-introduction-to-the-command-line-macs` is the *argument*.

`~` is a special path on Unix systems. It resolves to the logged-in user's *home directory*, which is the parent folder for configuration files as well as files they create. On a Mac system, user home directories live under `/Users`.

`/Users` begins with a `/` character, so it's an *absolute path*.

Are we in the right directory? Check by running `ls` to list its contents:

```
ls
```

You should see the files `README.md` and the directory `tutorial`.


Let's change into the tutorial directory:

```
cd tutorial
```

Note that `tutorial` doesn't begin with a `/`, it's a *relative path*, that is, relative to the directory we were in when we ran the command, i.e. the *working directory*.

On many systems, you'll likely see the *command prompt*, the text at the beginning of each line where you enter commands change to reflect your current directory. This is fully customizable, and something that people who use the shell a lot spend a lot of time tweaking.

We can see the contents of this directory, again using:

```
ls
```

You should see a `README.md` file and a `data` directory.

While we're here let's open the current folder in finder, so you can open some of the helper files in a text editor if you want to jump ahead, look back or get help. We'll use the `open` command:

```
open .
```

This should open a Mac Finder window for the current directory. You might want to double click on the files `README.md` to open this file in a text editor, as well as `solutions.md`.

The `.` is a special file path that means "the current working directory."

Let's change back to the directory where we were before, or the *parent* of the current working directory.

There's a special way to reference the parent of the current working directory. It's `..`.

So to change to the parent directory:

```
cd ..
```

So far, we've been changing directories with `cd` and listing the contents of the current working directory with `ls`. 

But, you don't have to change into a directory to list its contents, you can provide it as an *argument* the the `ls` command. Let's list the contents of the `tutorial` directory from our current directory:

```
ls tutorial
```

You can specify multiple levels of relative paths:

```
ls tutorial/data
```

As well as absolute paths:

```
ls /
```

There are also a number of *options* to the `ls` command. Let's use the `-l` option to see details about the files in the `tutorial` directory:

```
ls -l tutorial
```

You can provide multiple options. Let's use the `-l` option, along with `-h` to print file sizes in a more readable unit and `-a` to show hidden files:

```
ls -a -l -h tutorial
```

You can also just type the options smooshed up together:

```
ls -alh tutorial
```

The result is the same.

So far, we've been doing a lot of typing. We can save some by using the shell's filename generation feature.

Using `*` in a command argument that specifies a file or directory path tells the shell to match any character.

So,

```
ls tut*
```

shows the same output as if we had typed out `ls tutorial` because `tutorial` is the only child of the current working directory that begins with `tut`.

You can use `*` anywhere in your command argument.

As another example, let's list only the Markdown files in the `tutorial` directory, i.e. the files that end with `.md`. 

```
ls tutorial/*.md
```

There's another way to save typing when using the command line. It's called tab completion.

Type

```
ls tu<tab>/d<tab>/c<tab>
```

This should result in this command showing up in your shell:

```
ls tutorial/data/census-bureau-popest
```

What happens when there are multiple paths that match what you've typed so far? For example:

```
ls tutorial/data/census-bureau-popest/20<tab>
```

### Try it yourself 

Change directory to the `tutorial` directory.

Using `ls` or a combination of `cd` and `ls`, what is the most recent fiscal year for which ICE detention statistics are available?

## Creating and modifying files

### What we're learning

We're going to use these commands to create and modify files and directories.

- `mkdir` creates a directory.
- `touch` creates an empty file.
- `mv` renames a file or directory or moves a file into a different directory.
- `cp` copies a file or directory.
- `rm` deletes a file.
- `rmdir` deletes an empty directory.

### Try it together

First, let's make sure we're in the `tutorial` directory. Remember, we can use `pwd` to show the current working directory.

Let's make some (empty) data files. But first we need a place to put it. Let's create a directory for manually-edited data.

```
mkdir data/manual
```

Let's create some empty text files with the `touch` command:

```
touch data/manual/mok_data_1.txt
touch data/manual/mok_data_2.txt
```

Oops, we had a typo. Let's rename the files using the `mv` command. Using *tab completion* is really going to help here:

```
mv data/manual/mok_data_1.txt data/manual/mock_data_1.txt
mv data/manual/mok_data_2.txt data/manual/mock_data_2.txt
```

We might have more kinds of manually created data, so let's put these in a subdirectory. First we have to make it:

```
mkdir data/manual/mock_data
```

Then we can move the files into this new directory:

```
mv data/manual/mock_data_*.txt data/manual/mock_data
```

Let's make another file by copying one of the existing ones:

```
cp data/manual/mock_data/mock_data_1.txt data/manual/mock_data/mock_data_3.txt
```

Actually, this is all a terrible idea. Let's delete the files we created, and the directory:

```
rm data/manual/mock_data/mock_data_*
rmdir data/manual/mock_data
```

We changed our mind again. If only there were a way to re-run previous commands. Luckily, there is!

We can see recent commands by running:

```
history
```

We can page through previous commands by using the up and down arrow keys. Use the up arrow key until `mkdir data/manual/mock_data` appears. Then press the `<return>` key.

This could still be difficult if the command history can be quite long. You can also search through the history using `<ctrl>+r`.

Type

```
<ctrl>+rto
```

This should cause `touch data/manual/mok_data_2.txt` to appear at the prompt.

Typing `<ctrl>+r` again repeats the search backwards. 

This should cause `touch data/manual/mok_data_1.txt` to appear at the prompt.

Use the arrow and `<delete>` keys to edit the command so it reads `touch data/manual/mock_data/mock_data_1.txt`. Press the `<return>` key to run the command.

### Try it yourself

Typing the minimal number of characters, delete the file `data/manual/mock_data/mock_data_1.txt` and delete the directory `data/manual/mock_data`. 

## Viewing and previewing files

### What we're learning

We're going to use these commands to preview and get statistics about files. 

- `cat` shows the contents of a text file.
- `head` shows the first lines of a text file.
- `tail` shows the final lines of a text file.
- `less` shows the contents of a text file, one "page" at a time.
- `wc` counts the number of words, characters or lines in the file.

### Try it together

Let's look at the contents of a CSV file using the `cat` command. Run:

```
cat data/tucson/Tucson_Policy_Activity_2025_-2838525216610825691.csv
```

This shows all of the lines of the CSV file, but they scroll by really quickly. Let's look at a more managable chunk, the first lines of the file using the `head` command.

```
head data/tucson/Tucson_Policy_Activity_2025_-2838525216610825691.csv
```

To see fewer lines, specify the number of lines with the `-n` option:

```
head -n 6 data/tucson/Tucson_Policy_Activity_2025_-2838525216610825691.csv
```

The `tail` command works similarly, showing the final lines of the file.

```
tail -n 5 data/tucson/Tucson_Policy_Activity_2025_-2838525216610825691.csv
```

To view the contents of the file, bit by bit, use the `less` command:

```
less data/tucson/Tucson_Policy_Activity_2025_-2838525216610825691.csv
```

Once in the program, you can use `<space>` to view the contents forward one page at a time. `b` will move backwards in the file one page at a time. Using arrow keys will move forward and backward one line at a time.

Typing `/` followed by a pattern, will take you to the first instance matching the pattern in the forward direction. Then, `n` will repeat that search. `N` will repeat that search in the backward direction.

Typing `q` will exit `less`.

To get the number of rows in a file, use `wc`:

```
wc -l data/tucson/Tucson_Policy_Activity_2025_-2838525216610825691.csv 
```

### Try it yourself

What was the type of the first incident in the Tucson Police Activity CSV file on February 1, 2025?

## Searching for files and their contents

### What we're learning

We're going to use these commands to search for files that are named with certain patterns and try to find lines that match patterns within the files.

- `find` identifies files under a certain path matching specified patterns.
- `grep` searches the contents of text files based on patterns.
- `man` tells us about most command's syntax, options and usage.

### Try it together

Let's see if there are any data files that are FOIA logs in our data directory.

Before we start, make sure we're in the `tutorial` subdirectory. Recall that we can use `pwd` to see where we are and `cd` to get to the `tutorial` directory if we're not already there.

We'll use the `find` command to see if there are any files whose name contains "foia" in the data directory.

Note that `find` has a syntax that is a bit different than most other programs. The positional argument, which is the path where `find` should start searching comes before the option, `-name`, which specifies the filename pattern.

Also note the `*` wildcard that we learned about before. In this case, it's saying match file names with "foia" anywhere in the name. We have to put this pattern inside quotes because without it, the shell would try to expand matching filenames in the current directory, which is how we used `*` before. In this case, we're providing a pattern to the `find` command rather than having the shell interpret the pattern, so we quote the pattern.

This is one of the challenges of learning the command-line. You'll see similar syntax and patterns that function somewhat differently and are used in contexts that are subtly different. We can't get into all the potential cases where this is confusing, but just be aware this is common when troubleshooting problems.

```
find data -name '*foia*'
```

This didn't return many results. Let's try making the name pattern search case-insensitive.

```
find data -iname '*foia*'
```

That's better. We get a list of all the files that have "foia", regardless of case, somewhere in their name.

How did we know about the `-iname` option? You could search the web for this information, but Macs and other Unix systems have built-in manual pages for most commands. To view them, use the `man` command:

```
man find
```

We can navigate the results using the same keystrokes we learned with `less`. Recall that you can type `q` to quit.

The manual pages are dense and long, but you will learn so much by skimming or reading the whole thing. If I can't wait, I will often use the `/` key to search and jump directly to the "EXAMPLES" section that's present in most commands' manual pages.

### Try it yourself

How would you find only FOIA logs for 2024 that are in the CSV file format?

### Try it together

So far, we've learned how to search for file names matching a pattern, but what if we want to search their contents?

We can use the `grep` command to search for lines matching certain patterns in a text file. 

Let's see if we can find out if any of the records requests in the CSV versions of the ICE FOIA logs mention "Tucson" with this `grep` command:

```
grep -i 'tucson' data/ice-foia-logs/*.csv
```

Note that the `-i` tells `grep` to do a case-insensitve search, so we'll match "Tucson" as well as "TUCSON" (or "TuCSoN"). We don't have to quote "tucson" in this example, but it's a reminder that it's a pattern and that we might need to use quotes if we include any special characters like `*` in the pattern. 

From the output of grep, we can see that it shows the path of the matching file and the matching line.

If we only want to see the names of the files that match, rather than one line of output per matching line, we can use

```
grep -il 'tucson' data/ice-foia-logs/*.csv
```

In the `grep` commands we've typed so far, we've provided a specific list of files for `grep` to search. We can also use the `-r` option to tell it to *recursively* search all files and all files in subdirectories under a particure path:

```
grep -ilr 'tucson' data
```

### Try it yourself

Use a different pattern to search the FOIA log CSV files for something of interest to you. What did you find?

## Redirecting input and output

### What we're learning

We're going to use these commands to experiment with redirecting the output of one program to another, or to a file:

- `in2csv` converts many data file formats to CSV.
- `csvgrep` works like `grep`, but in a way that is aware of data's structure.
- `csvformat` reformats delimited text files, e.g. converting CSV to TSV.
- `pbcopy` copies its input to the system clibboard.

We're going to learn about these concepts:

- *Standard output* is the place where commands send their output.
- Using the `|` (pipe) operator to redirect the output of one program into the input of another.
- Using the `>` operator to redirect the output of a program to a file.
- Using the `-h` or `--help` option to get command help.

### Try it together

Many FOIA requesters to ICE are lawyers, not journalists. Let's try too see all the rows of the FOIA log CSVs that might be from lawyers:

```
grep -i 'law' data/ice-foia-logs/*.csv
```

There are a lot of matches, and they scroll by really fast. 

That's because `grep` is sending the results of the command to *standard output*, which we see in the terminal.

How can we look at the output in a more leisurely way? 

Let's send the output of the `grep` command to the pager program `less` that we used before instead of to *standard output*:

```
grep -i 'law' data/ice-foia-logs/*.csv | less
```

Now we can page through the output of `grep` using the keystrokes we learned before. Remember, type `q` to quite out of `less`.

So much of data journalism is just counting things. We can use a few things we've learned so far to get really quick signals about data, without needing something like a pivot table. Let's see how often "tucson" is mentioned in the FOIA logs by combining `grep` and `wc`:

```
grep -i 'tucson' data/ice-foia-logs/*.csv | wc -l
```

From this, we can see that Tucson is mentioned two times.

We can also redirect the output of a command to a file. 

I often use the `in2csv` command, which is part of the [csvkit](https://github.com/wireservice/csvkit) package, a set of programs for working with CSV files and other tabular data data in text format, to convert from Excel to CSV.

Let's try doing this with one of the Excel FOIA logs that hasn't already been converted to CSV:

```
in2csv data/ice-foia-logs/FY2024_FOIA_AppealsLog.xlsx 
```

That command outputs the CSV to *standard output*, but we might want to have the data in CSV format for later. We can redirect the output to a file using the `>` operator.

```
in2csv data/ice-foia-logs/FY2024_FOIA_AppealsLog.xlsx > data/ice-foia-logs/FY2024_FOIA_AppealsLog.csv
```

So far, we've worked a bit with CSV files and searching them with `grep`, but `grep` doesn't have any concept of the columns of the data. That is, we can't limit our search to certain columns. Luckily, csvkit also includes a program called `csvgrep` that works like `grep` but thinks in terms of the data's structure.

Let's modify a `grep` command we used earlier to search for Tucson only in the `Request Description` column:

```
csvgrep -c 'Request Description' -m "Tucson" data/ice-foia-logs/2024-08_FOIA_Log.csv
```

Note that `csvgrep` only works on a single file at a time and also includes the header row in the output. The search is also case-sensitive, though there is a [way to specify case insensitve patterns](https://github.com/wireservice/csvkit/issues/248#issuecomment-32101897).

How do we learn about the options of `csvgrep` when `man csvgrep` doesn't seem to work. In addition to *manual pages*, many commands have a help option which, when specified, will show help text. Conventionally, this option is `-h` or `--help`:

```
csvgrep -h
```

You may see from this output that many options have both a short version that is one character preceded by a `-` and long version, which is preceded by `--`. For example, `-c` and `--columns` do the same thing, they specify the columns to search. The short version is faster to type, while the long version gives the reader of a script or data diary a better idea of what the command is doing if they're not familiar with a particular program. 

One thing I do all the time is share slices of data with others. Let's start by *piping* the output of `csvgrep` to `csvformat` to convert it to a tab-separated format:

```
csvgrep -c 'Request Description' -m "Tucson" data/ice-foia-logs/2024-08_FOIA_Log.csv | csvformat -T
```

Note that I used the short version of the option that outputs tabs instead of commas, `-T`, but I could have also used `--out-tabs`.

What if I wanted to bring this into a spreadsheet program like Excel or Google Sheets?

I can redirect the output to a program called `pbcopy` that copies the text to the system clipboard that can then be pasted into the spreadsheet.

```
csvgrep -c 'Request Description' -m "Tucson" data/ice-foia-logs/2024-08_FOIA_Log.csv | csvformat -T | pbcopy
```

Note that this pipeline has three steps whereas before we only had two. We can connect the inputs and outputs of programs using `|` in pipelines that could be many steps. But each step might be a very simple command. This helps experimenting and testing with each part of the pipeline.

### Try it yourself

Use `csvgrep` to find requests that match "Law" in the `Requester::Organization Name` column of `data/ice-foia-logs/2024-10_FOIA_Log.csv` and use `csvcut` to display only that column. Save this to a file named `data/ice-foia-logs/2024_lawyer_requests.csv`.

Bonus points: Use `uniq` and `csvsort` to get only unique lawyer/law firm names. Then count the number of unique names.
