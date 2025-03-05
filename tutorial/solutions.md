# Introduction to the command line tutorial solutions

## Navigating the filesystem

Change directory to the `tutorial` directory.

```
cd tutorial
```

Using `ls` or a combination of `cd` and `ls`, what is the most recent fiscal year for which ICE detention statistics are available?

To do this using just ls:

```
ls data
ls data/ice-detention-statistics/
```

You should see a listing like this:

```
FY19-detentionstats.xlsx         FY21-detentionstats.xlsx         FY23_detentionStats.xlsx         FY25_detentionStats02142025.xlsx
FY20-detentionstats.xlsx         FY22-detentionStats.xlsx         FY24_detentionStats.xlsx         FY25_detentionStats02272025.xlsx
```

From the filenames, the most recent fiscal year of data appears to be 2025, and there are two files:

- `FY25_detentionStats02142025.xlsx`
- `FY25_detentionStats02272025.xlsx`

You could also have descended into the directory structure, and ran `ls` at each step:

```
ls
cd data
ls
cd ice-detention-statistics
ls
```

That's a big more work however. Make sure you change directory back to where you started:

```
cd ../..
```

## Creating and modifying files

### Try it yourself

Typing the minimal number of characters, delete the file `data/manual/mock_data/mock_data_1.txt` and delete the directory `data/manual/mock_data`. 

The least typing would be to type `<ctrl>+r` and then `rm `, which causes the command `rm data/manual/mock_data/mock_data_*` to appear.

Then, type `<ctrl>+r` and then `rmd`, which causes the command `rmdir data/manual/mock_data` to appear.

You could have also used the up arrow key to find these commands.

The longest way to complete this task would be to type out these commands.

## Viewing and previewing files

### Try it yourself

What was the type of the first incident in the Tucson Police Activity CSV file on February 1, 2025?

Use less to view the file:

```
less data/tucson/Tucson_Policy_Activity_2025_-2838525216610825691.csv
```

Then, type the `/` character to search and type `2/1` and `<return>` to jump to the first record where the `EventDate` is "2/1/2025". The `EventType` value is "Moving Violation".
