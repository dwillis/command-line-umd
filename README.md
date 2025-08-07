# Introduction to the command line

This is a tip sheet and interactive activity for a hands-on session about using the command line with GitHub Codespaces.

The goal is to offer a fundamental, but hopefully not too basic introduction to using command-line programs in a cloud-based environment. I'm trying to focus on areas where I've seen people struggle with using command-line programs in the newsroom. 

## Assumptions

This tutorial is intended for use with GitHub Codespaces, which provides a Linux-based development environment in your web browser.

If you have your own computer running Mac OS or Linux (including under the Windows Subsystem for Linux), you should be able to follow along with minor modifications.

If you're using a Windows computer without the Windows Subsystem for Linux or a tablet device such as an iPad, GitHub Codespaces will provide you with a better experience than trying to run these commands locally.

The tutorial portion is oriented around the Bash shell, which is the default in GitHub Codespaces. Most, if not all, of the examples in the tutorial should work on other shells, but if you encounter errors, that may be the reason.

Finally, some of the examples in the tutorial use [csvkit](https://github.com/wireservice/csvkit), which will be automatically installed when you create your Codespace.

## Getting Started with GitHub Codespaces

1. **Open this repository in GitHub Codespaces:**
   - Click the green `Code` button on this repository's GitHub page
   - Select the `Codespaces` tab
   - Click `Create codespace on main`
   - Wait for the environment to load (this may take a minute or two)
   - csvkit will be automatically installed during setup

2. **Open the terminal:**
   - Once Codespaces loads, you'll see VS Code in your browser
   - Open a terminal by clicking `Terminal` > `New Terminal` in the menu bar
   - Or use the keyboard shortcut `Ctrl+Shift+\`` (backtick)

3. **Navigate to the tutorial:**
   ```bash
   cd tutorial
   ```

4. **Start the tutorial:**
   - Open `tutorial/README.md` in the VS Code editor to follow along
   - You can also view `tutorial/solutions.md` for reference

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

### Tucson Police Department Police Activity Open Data for 2025

Agency: Tucson Police Department

Link: [Tucson Policy Activity 2025](https://gisdata.tucsonaz.gov/datasets/d0092810c2ea45ff938ae1c5b43c7b4a_0/explore)
