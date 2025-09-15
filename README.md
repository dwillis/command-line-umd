# The greatest introduction to the command line!!

This is a template repository for a hands-on session about using the command line with GitHub Codespaces. Create your own copy using the "Use this template" button above.

The goal is to offer a fundamental, but hopefully not too basic introduction to using command-line programs in a cloud-based environment. I'm trying to focus on areas where I've seen people struggle with using command-line programs in the newsroom. 

## Assumptions

This tutorial is intended for use with GitHub Codespaces, which provides a Linux-based development environment in your web browser.

The tutorial portion is oriented around the Bash shell, which is the default in GitHub Codespaces. Most, if not all, of the examples in the tutorial should work on other shells, but if you encounter errors, that may be the reason.

Finally, some of the examples in the tutorial use [csvkit](https://github.com/wireservice/csvkit), which you'll install after you create your Codespace.

## Getting Started with GitHub Codespaces

1. **Create your own repository from this template:**
   - Click the green `Use this template` button at the top of this repository's GitHub page
   - Select `Create a new repository`
   - Give your repository a name (e.g., `my-command-line-tutorial`)
   - Make sure it's set to `Public` (required for free Codespaces usage)
   - Click `Create repository from template`

2. **Open your new repository in GitHub Codespaces:**
   - Navigate to your newly created repository
   - Click the green `Code` button on your repository's GitHub page
   - Select the `Codespaces` tab
   - Click `Create codespace on main`
   - Wait for the environment to load (this may take a minute or two)
   - csvkit will be automatically installed during setup

3. **Open the terminal:**
   - Once Codespaces loads, you'll see VS Code in your browser
   - Open a terminal by clicking `Terminal` > `New Terminal` in the menu bar
   - Or use the keyboard shortcut `Ctrl+Shift+\`` (backtick)
   - Copy and paste this command into the Terminal:

   ```bash
   go install github.com/maaslalani/slides@latest
   ```

   It will take a minute to run. You won't have to do it again.

4. **Navigate to the tutorial:**
   ```bash
   cd tutorial
   ```

5. **Start the tutorial:**
   - Open `tutorial/README.md` in the VS Code editor to follow along
   - You can edit this file directly to record your answers as you work through the exercises
   - You can also view `tutorial/solutions.md` for reference

6. **Tutorial reflection:**
   At the end of this README, answer the following questions:
   - How could command line skills improve your efficiency as a journalist?
   - What types of stories or investigations would benefit most from these tools?
   - What felt most challenging about learning these technical skills?
   - How does this connect to your understanding of data journalism?

## What's in here?

- `tutorial`: Instructions and data for the hands-on activity we'll walk through during the conference session. You should also be able to follow along on your own computer.
- `tutorial/slides.md`: Slides used during the conference session. These can be displayed using the [slides](https://github.com/maaslalani/slides) tool.
- `tipsheet.md`: General tips and links to other references for using the command line.

## Data sources

The command line is by no means a set of tools and concepts specific to journalism. I've tried to use real data in this tutorial to ground the concepts in the kinds of ways I use the command line as a data reporter.

### ICE Detention Statistics 

Agency: U.S. Immigration and Customs Enforcement

Link: [Detention Management | ICE](https://www.ice.gov/detain/detention-management)

### National Population Totals and Components of Change: 2010-2019

Agency: U.S. Census Bureau

Link: [National Population Totals: 2010-2019](https://www.census.gov/data/tables/time-series/demo/popest/2010s-national-total.html)

### National Population Totals and Components of Change: 2020-2024

Agency: U.S. Census Bureau

Link: [National Population Totals: 2020-2024](https://www.census.gov/data/tables/time-series/demo/popest/2020s-national-total.html#v2023)

### UMPD Incident Logs

Agency: UMPD

Link: [UMPD Incident Logs](https://umpd.umd.edu/statistics-reports/daily-crime-and-incident-logs)
