# Introduction to the command line tutorial

If you get stuck during the try it yourself portions, take a look at `solutions.md`.

There's some information about the commands we'll be using 

## Navigating the filesystem

### What we're learning 

We're going to use these commands to move across the filesystem or learn where we are:

- `cd`: Change directory to a different directory on your filesystem.
- `pwd`: Print the current working directory.
- `ls`: List files in the current working directory or a specified path.

We'll also learn about these concepts:

- *Absolute* and *relative* *paths*
- *Arguments* to *commands*
- *Command* *options*
- Using filename generation and the `wildcard` symbol.
- *Tab completion*

### Try it together

Check what directory you're in by running:

```
pwd
```

Change directory to the project root directory. At NICAR 2025, on the lab computers, this will be `TK`. On my computer, this is `/Users/ghing/workspace/nicar-2025-command-line`.

```
cd TK
```

In this case `cd` is the *command* and `TK` is the *argument*.

The path begins with a `/` character, so it's an *absolute path*.

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

We can see the contents of this directory, again using:

```
ls
```

You should see a `README.md` file and a `data` directory.

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
ls t<tab>/d<tab>/c<tab>
```

This should result in this command showing up in your shell:

```
ls tutorial/data/census-bureau-popest
```

What happens when there are multiple paths that match what you've typed so far? For example:

```
ls tutorial/data/census-bureau-popest/2<tab>
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
