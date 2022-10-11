<sub>℗Key or Pirate Key is a color theme<br> for testing <a href="https://marketplace.visualstudio.com/items?itemName=maxagin.p-key&ssr=false#overview
" target="_blanck">DVC Extension for Visual Studio Code</a> multiple theme compatibility.</sub>

&nbsp;

<p align="center">
<img width="230" alt="P Key icon" src="https://user-images.githubusercontent.com/98249521/194963804-f3e217f2-769d-4563-bd50-3c90e59b1e9a.png">
</p>

<h1 align="center">℗Key</h1>
<p align="center">For pirates of Visual Studio Code.</p>

<sub>
<p align="center">"tab.activeBackground": "#f3361f",
"panel.border": "#4a1d1c",
"foreground": "#4a1d1c",
//"disabledForeground": "#4a1d1c",
"button.background": "#dd2108",
"dropdown.background": "#4a1d1c",
//"widget.shadow": "#000000",
//"descriptionForeground": "#fff",
"sash.hoverBorder": "#fff",
"editor.background": "#f3361f",
"editor.foreground": "#4a1d1c",
"editorLineNumber.foreground": "#4a1d1c",
"sideBar.background": "#f3361f",
"sideBar.border": "#4a1d1c",
"activityBar.activeBackground": "#f3361f",
"activityBar.activeBorder": "#f3361f",
"statusBar.background": "#dd2108",
//"statusBar.border": "#4a1d1c",
"activityBar.background": "#dd2108",
//"activityBar.border": "#4a1d1c",
"editorGroupHeader.tabsBackground": "#25252d",
"terminal.background": "#f3361f",
"quickInput.background": "#f3361f",
"editorCursor.foreground": "#ffff00",
"terminalCursor.foreground": "#ffff00",
"focusBorder": "#4a1d1c",
// "settings.rowHoverBackground": "#fff",
"scrollbarSlider.background": "#4a1d1c",
"notifications.background": "#f79c18",</p>
</sub>

&nbsp;

<sub><p align="center">Minimalistic</p></sub>

&nbsp;

<!--
<img width="1500" alt="P Key cover art" src="https://user-images.githubusercontent.com/98249521/194963601-752bb18c-841c-4904-b140-014254f7788d.png">
-->
<img width="1500" alt="P Key cover art" src="https://user-images.githubusercontent.com/98249521/194971403-aef31a97-a19b-4527-8dc3-63523a153bfb.png">


<!--

<sub>
Helprull information:<br>
Toggle preview (`Shift+Cmd+V` on macOS or `Shift+Ctrl+V` on Windows and Linux).<br>
[Visual Studio Code's Markdown Support](http://code.visualstudio.com/docs/languages/markdown)<br>
[Markdown Syntax Reference](https://help.github.com/articles/markdown-basics/)
</sub>

-->

<sub>
In order to track the data files and directories added with dvc add, dvc repro, etc. DVC moves all these files to the project's cache. 

However, the versions of the tracked files that match the current code are also needed in the workspace, so a subset of the cached files can be kept in the working directory (using dvc checkout). Does this mean that some files will be duplicated between the workspace and the cache? 

That would not be efficient! Especially with large files (several Gigabytes or larger). 

In order to have the files present in both directories without duplication, DVC can automatically create file links to the cached data in the workspace. In fact, by default it will attempt to use reflinks* if supported by the file system. File link types for the DVC cache File links are lightweight entries in the file system that don't hold the file contents, but work as shortcuts to where the original data is actually stored. 

They're more common in file systems used with UNIX-like operating systems, and come in different kinds that differ in how they connect file names to inodes in the system. Inodes are metadata file records to locate and store permissions to the actual file contents. 

See Linking files in this doc for technical details (Linux). Use ls -i to list inodes on Linux. 

There are pros and cons to the 3 supported link types: Hard links, Soft or Symbolic links, and Reflinks in more recent systems. While reflinks bring all the benefits and none of the worries, they're not commonly supported in most platforms yet. Hard/soft links optimize speed and space in the file system, but may break your workflow since updating hard/sym-linked files tracked by DVC in the workspace would cause cache corruption. 

To protect against this, DVC protects hardlinks and symlinks by making them read-only, requiring using dvc unprotect to be able to modify them safely.
</sub>

