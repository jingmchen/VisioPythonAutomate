# VisioPythonAutomate
Python application to batch process Visio files based on user defined rules.

Created for a previous company. IP belongs to the company. Thus, no code or screenshots will be shown (due to IP laws). Software name has been renamed (due to IP laws)

# Problem Statement
I discovered that the team was doing annotation on Visio files manually for hundreds of Visio files.
There was no software or automation tool to speed up manual annotation efforts

I quickly developed a Python script which eventually scaled to a full application.

Idea: Me, Programming (Backend and Frontend): Me, Bugtesting: Me

# What was created
A Python application (exe) with Python313.dll bundled within so that users do not need to install Python to use it.

On first run, seeds filters (json) and settings.json to %LOCALAPPDATA%

On app launch, shows TERMS and CONDITIONS window waivering liability from me if any errors or business losses occurs as a result of misuse by the end user.

When user clicks agree, they would go to the MainWindow whereby they can multiselect Visio files (*.vsdx) to be processed. They can also configure the rules for the processing:
a. REMOVE filter (REMOVE.json)
b. REPLACE filter (REPLACE.json)
c. CONDITIONAL filter (CONDITIONAL.json)
d. SWITCH filter (SWITCH.json)

When they clicked a new button to edit the rules, it goes to a new window with tabs for each filter. There are multiple rules for each filter, and they can be ranked by priority (which fires first)

Rules fires off using Regular Expression with wild cards, local variables {0}, and global variables {{0}} features with REMOVE (strikethrough without replacement), REPLACE (strikethrough with replacement text), CONDITIONAL (strikethrough with replacement text with an anchored conditional operator such as OR, NOT), and SWITCH (strikethrough with replacement text depending on a user-specified SWITCH parameter variable fetched through compiled RegExp pattern)

Visio files are essentially packaged ZIP files with XML files within. However, I am annotating the Text XML block which contains human readable words. Thus, after XML parsing to reach Text XML block for each Shape XML block in each page, Regular Expression patterns are used to match each rules (compiled to RegExp pattern) against the strings in the Text XML block.

By the way, I am not sure why < and > do not render correctly in Github markdowns

# My Development
At first, I developed a quick Python script to automate tedious parts of the annotation for me. As I annotated more files, I realized a lot of rules slipped through and I needed a new refactoring to make the software more scalable.

Quickly, I realized I spent too much time on this personal tool, and thus decided to contribute it to the team.

To do so, I needed to convert a console-ran script to a full-scale application

Fortunately, I have software development experience in C# thus this was not difficult.

I needed to bundled all the files into an application, which I used pyinstaller.

Next, the rules (REMOVE, REPLACE..) needed to be editable not in JSON format, but in a user-friendly UI

Finally, I need heavier error handling and default fallbacks, as the team do not know how to use Python.

Also, I used an app.ico from CC0.
