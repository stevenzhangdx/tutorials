
# VS Code
- [VS Code](#vs-code)
    - [Extensions, User Settings, and the Command Pallete](#extensions-user-settings-and-the-command-pallete)
    - [General Setup](#general-setup)
    - [Setup for Julia](#setup-for-julia)
    - [Github Integration](#github-integration)
    - [Setup for Latex](#setup-for-latex)
    - [Other Links and Material](#other-links-and-material)

Another cross-platform, general purpose editor with Julia support is [VS Code](https://github.com/Microsoft/vscode)

## Extensions, User Settings, and the Command Pallete
**Command Palette:** 
Many features in VS Code are found through the Command Palette which can be accessed with `Ctrl+Shift+P`.  Throughout, these notes on OSX the `Ctrl` is the `⌘` button.  See https://code.visualstudio.com/docs/getstarted/userinterface for more on the VS Code UI.

**Extensions:** Go to the Extensions tab by clicking on the left side of VS Code, or `Ctrl+Shift+X`.  To find an extenion, type in part of the name into `Search Extensions in Marketplace`.  Alternatively, you can directly click "Install" button on the web links in the VS Code Marketplace

**User Settings:** To edit [Settings](https://code.visualstudio.com/docs/getstarted/settings) in VS Code, open up the user settings with `Ctrl+,` or opening up the command palette and starting to type `User Settings`.To find a particular settings, start typing in the name of the setting, extension, etc. Once you find it, you can select the `Edit` icon next to a particular setting to copy it to your local settings, and change it.

## General Setup
1. Install [VS Code](https://github.com/Microsoft/vscode)
2. *Optional*: Install [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) 
    - Not required, but a good idea since [Markdown](markdown.md) is pervasive
    - For TOC compatability with github, go to the User Settings with `Ctrl+,` and then set `"markdown.extension.toc.githubCompatibility": true`
    - To have it show a preview immediately when you open one of the files, set `"markdown.extension.preview.autoShowPreviewToSide": true`
3. *Optional:* It is convenient to globally change the word wrap, so choose `Ctrl+,` and then set `"editor.wordWrap": "on",
4. *Optional*: Install the [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) extension.

## Setup for Julia
1. Ensure that [VS Code](https://github.com/Microsoft/vscode) and [Julia](julia.md) are installed
2. Type in `julia` to find and install `Julia Language Support`
    - Alternatively, you can click `Install` from [VS Code Julia](https://marketplace.visualstudio.com/items?itemName=julialang.language-julia)
3. To test the installation:
    - Create a new File called `test.jl` or something similar, and copy in something like
    ```julia
    f(x) = x
    f(2)
    ```
   - In the file, go `F5` to run the file.  The first time you do this, it is likely that this will take time so be a little patient.  On the bottom, it may say something like "Language Server Busy"
   - If it shows something in the bottom "TERMINAL" like the following, then it is working
    ```julia
    Main> f(x) = x
    f (generic function with 1 method)
    Main> f(2)
    2
    ```
4. *Optional*: If the above doesn't work, then you may need to manually set your Julia executable.
    - First, find the location of the julia binary.  The easiest way to do this is to open a separate Julia REPL and type `JULIA_HOME` to get something like `C:\\Users\\jlperla\\AppData\\Local\\Julia-0.6.3\\bin`
    - From this location, the file is something like `C:\\Users\\jlperla\\AppData\\Local\\Julia-0.6.3\\bin\\julia.exe` on Windows or something equivalent on other OSs.  For Windows, make sure to double every backlash
    - To set this in VS Code, open up the user settings by opening up the command palette `> Preferences: User Settings`
    - In here, type `julia` to get the julia specific settings
    - Then click on the "julia.executablePath" in the "Default User Settings" and choose "Edit" to "Copy to Settings"
    - This copies it over, and you can put in the path.  For example, `"julia.executablePath": "C:\\Users\\jlperla\\AppData\\Local\\Julia-0.6.3\\bin\\julia.exe"` where the quotes are important.
5. Play around with executing Julia code
    - You can execute a single line with `Ctrl+Enter`, which is a great way to go line by line through the code
    - Execute the whole file with `F5`
    - To see the plotting pane, ensure you have `Plots.jl` installed (i.e. `Pkg.add("Plots")`) and then copy the following into a test file
    ```julia
    using Plots
    plot(1:5, 1:5)
    ```
    - Execute the code (noting that `using Plots` the first plot will take 20-30 seconds after precompilation) and it should show the Plot Pane
6. *Optional, but strongly encouraged:* Setup the `Revise.jl` workflow described in [Julia Notes](julia.md#advanced-configuration-for-your-desktop-the-revise-workflow).  To summarize,
    - Find the `.` files are for your account. For example, it is usually at cd ~ on linux/osx/windows with bash, or in a directory such as `C:\Users\jlperla`
    - Copy [.juliarc.jl](etc/.juliarc.jl) to that directory or add the contents of that file if required.

## Github Integration
- If you are working on a cloned repository, you can see changes in the `Source Control` tab, or with `Ctrl+Shift+G`.
- This will show you changes to the files, etc.  It will let you `Commit` with a message as well.
- The left hand side of the bottom bar on VS Code (or the Git repository in this tab) will let you Pull/Push/Sync
- A simple [Tutorial](https://www.youtube.com/watch?v=9cMWR-EGFuY) with more detail in [Using Version Control in VS Code](https://code.visualstudio.com/docs/editor/versioncontrol)

## Setup for Latex
1. If you just did the Julia setup, perhaps restart so you don't have the same windows cluttered.
2. *Optional*: While TeXLive already has it, if you have installed `MikTex` on Windows, you will need to manually setup SyncTex:
    - Download [kpathsea630.dll](https://www.tug.org/svn/texlive/trunk/Master/bin/win32/kpathsea630.dll?revision=46993&view=co)
    - Download [synctex.exe](https://www.tug.org/svn/texlive/trunk/Master/bin/win32/synctex.exe?revision=46993&view=co)
    - And place both of them in the miktex binaries folder, e.g. `C:\Program Files\MiKTeX 2.9\miktex\bin\x64`
3. Install the following packages in VS Code (clicking on them or using `Ctrl+Shift+X` to get the extensions)
  - [LaTex Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
  - [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
4. At this point, you should be able to open a test latex file.  Create a `test.tex` file with something like
```tex
\documentclass{article}
\begin{document}
TEST
\end{document}
```
4. Then go `Ctrl+Alt+B` to build the file then `Ctrl+Alt+V` to get the PDF preview.
5. If you make a change in the latex (e.g. change to `TESTS`) and save, if should automatically update the PDF.
7. *Optional*: Many latex packages require a compilation settings with shell access.
    - To do this, open up the user settings, `Ctrl+,` and start searching for `latex-workshop.latex.magic.args`
    - Copy it to the `USER SETTINGS` and modify, adding in a `"-shell-escape",` line.  It should look something like,
    ```JSON
    "latex-workshop.latex.magic.args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-shell-escape",
            "-file-line-error",
            "%DOC%"
        ]
    ```
    - These settings are used whenever the magic comments are used in the latex file, e.g.
    ```tex
    % !TEX program = pdflatex
    % !BIB program = bibtex
    ```
8. *Optional:* For less irritating error messages, change to `"latex-workshop.message.error.show": false` and  `"latex-workshop.message.warning.show": false`

## Snippets 

### Project-Specific
Sometimes your project will have boilerplate code (like tests) that you need to use repeatedly. VSCode provides a nice syntax for creating and using these. 

1. Download the `Project Snippets` extension and install it. 
2. In your project folder (the same one with the `.git` directory), create a folder `./vscode/snippets`. 
3. Inside that folder, create a JSON file for every language you need custom snippets for (say, `julia.json`). The language names should be in lowercase. 
4. From there, you can use the following syntax (explained below). 

```
{
  "SnippetA": {
      "prefix": "blahblahblah",
      "body": [
        "for (const ${2:element} of ${1:array}) {",
        "",
        "}"
      ],
      "description": "For Loop"
  }
}
```

This defines a snippet, `SnippetA`. You access it by typing `blahblahblah` into the VSCode editor (or accessing the snippets menu with `Ctrl + Space`. From there, the boilerplate code will appear. The `${1:xyz}` has two pieces. The number governs where your keystrokes will fill first (so in this example, what I start typing immediately after loading the snippet will fill that spot, then if I hit `tab`, what I type next will fill the second spot, and so on). Lines should be separated by `,`s. The words `array` and `element` govern what appear in those spots before I start filling them in.

To create multiple snippets, simply place a `,` after the first one (i.e., after the second-to-last `}`, and repeat the code for the first one. It should have a different snippet ID (what we have as `SnippetA`). 

### Project-Independent

Sometimes, you'll have snippets which you want to use for a language in general, regardless of what project you're working on. 

To work on these, click `Preferences -> User Snippets`, select the appropriate snippets file, and repeat the same procedure as above. 

### Sharing Snippets

To share snippets, just copy and paste your `{language}.json` file to somebody.

## Other Links and Material
- [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync) is an extension to maintain settings between different computers.  A little complicated to setup
- https://github.com/formulahendry/vscode-code-runner is another package... not sure it is useful for Julia or Python
- In the menu, go to `Help/Interactive Playground` to see features such as Multi-Cursor Editing, etc.
- Lots of places in VSCode, you're asked to describe things in a format called JSON (snippets, preferences, etc.) If this format is unfamiliar to you, [this site](https://code.tutsplus.com/tutorials/understanding-json--active-8817) provides a friendly tutorial. 
