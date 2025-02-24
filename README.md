# Introduction to the command line

This is a tip sheet and interactive activity for a hands-on session about using the command line for the 2025 NICAR conference.

The goal is to offer a fundamental, but hopefully not too basic introduction to using command-line programs on Mac OS. I'm trying to focus on areas where I've seen people struggle with using command-line programs in the newsroom. 

## Assumptions

This tutorial is intended for Mac computers in the hands-on lab at the conference. 

If you have your own computer running Mac OS or Linux (including under the Windows Subsystem for Linux), you should be able to follow along.

If you're using a Windows computer without the Windows Subsystem for Linux or a tablet device such as an iPad, you're going to have a much more difficult time following along. You could try using [JSLinux](https://bellard.org/jslinux/), but no guarantees that everything will work correctly.

If you're following along on a non-lab system, you'll need to clone this repository.

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

## Starting over: Use `ctrl+c`

## Navigating the file system

## Anatomy of a command

## Editing and reusing commands

## Redirecting input and output

## Running commands on many inputs

## Next steps

- Environment variables
- Shell expansion
- Suspending and killing processes and running longrunning processes in parallel
- Using the command-line on other systems
- Installing command-line software

## Resources

- [AJVicens/command-line-for-reporters](https://github.com/AJVicens/command-line-for-reporters): Tip sheet from this session at a past NICAR conference. 
- [armendariz/terminal_recipes](https://github.com/armendariz/terminal_recipes): Tip sheet for a similar session from the 2015 NICAR conference.
- [chrislkeller/nicar15-command-line-basics](https://github.com/chrislkeller/nicar15-command-line-basics): Tip sheet from a different version of the 2015 NICAR conference.
- [TK]()
- [useful tools for the command line](https://docs.google.com/presentation/d/1TwQdzwfjrAaNxbVlkRa_2zn6UPOFFOkOcFOTb0mASTw/edit#slide=id.ga856f3037_028)
- [KarrieK/NICAR16](https://github.com/KarrieK/NICAR16): Tip sheet and tutorial for a similar session at the 2016 NICAR conference. This one is more focused on csvkit.
- [Command line crash course - Learn web development | MDN](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Environment_setup/Command_line)
