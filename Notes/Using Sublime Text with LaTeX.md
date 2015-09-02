Using Sublime Text 3 for Thesis Writing
=======================================

The reason I want to use Sublime for writing my thesis is that most LaTeX editors are very cluttered, with source text, pdf preview, project files, logs and errors, etc etc, filling up the screen. I find this distracting when writing and found the Sublime Text "Distraction Free Full Screen Writing" *phenomenal*, especially set at 72 or 80 characters wide. 

I was going to just write in Sublime Text and then compile in the shell, but a quick search showed there are two Sublime plugins for LaTeX writing with Sublime Text: LaTeXTools and LaTeXing. I will be trying out LaTeXTools, since the project is open source and seems to have many users, developers and seems stable.

Getting it up and running
-------------------------
* Download and install Sublime Text 3
* Download and install MiKTeX
* Download and install SumatraPDF

Get the LaTeXTools plugin. These days, the easiest way to do so is via Package Control: 
* Install the Package Control for Sublime Text
	- The console is accessed via the ctrl+` shortcut or the View > Show Console menu. 
	- Once open, paste the appropriate Python code for your version of Sublime Text into the console, found at https://packagecontrol.io/installation#st3
* Once you have Package Control up and running, invoke it (via the Command Palette from the Tools menu, or from Preferences), select the Install Package command, and look for LaTeXTools.
* If you are installing LaTeXTools for the first time, you need to create a configuration file, LaTeXTools.sublime-settings, in your User directory (off the Packages) directory. To do so, open the command palette from the Tools menu, search for “LaTeXTools: Reconfigure and migrate settings,” and hit Return. That's it! See the Settings section for details on configuration options.

Configure
---------
Follow the instructions on https://packagecontrol.io/packages/LaTeXTools 

As of today, these are:
On Windows, both MikTeX and TeXlive are supported.

* Add both MiKTeX and SumatraPDF paths to the Windows environment PATH variable, if they are not added already.
* Open a command-line console (run cmd.exe), and issue the following command:
	```sumatrapdf.exe -inverse-search "\"C:\Program Files\Sublime Text 2\sublime_text.exe\" \"%f:%l\"" ```
* Finally, edit the file LaTeX.sublime-settings in the User directory to make sure that the configuration reflects your preferred TeX distribution. Find it under Preferences > Package Settings > LaTeXTools > Settings - User.
 	- Open the file and scroll down to the section titled “Platform settings.” Look at the block for your OS, namely windows. Within that block, verify that the texpath setting is correct; for MiKTeX, you can leave this empty, i.e., "". If you do specify a path, note that it must include the system path variable, i.e., $PATH (this syntax seems to be OK). Also verify that the distro setting is correct: the possible values are "miktex" and "texlive".


Multi-file documents are supported as follows. If the first line in the current file consists of the text %!TEX root = <master file name>, then tex & friends are invoked on the specified master file, instead of the current one. 

### Important ###
For the ```\ref{ ``` and ```\cite``` commands to produce a pop-up with available labels and citations, *ALL* the documents included in the project must be saved with UTF-8 encoding! Otherwise it doesn't work correctly!


Displaying LaTeX nicely
-----------------------
Additionally, it is helpful to have a Color Scheme that displays LaTeX nicely. I have downloaded and tweaked one to my liking, by using the TmTheme-Editor at 
http://tmtheme-editor.herokuapp.com or https://github.com/aziz/tmTheme-Editor. 

The color scheme I've tweaked to my liking is the ```Light LaTeX Scheme.tmTheme```, which should be found in this same directory folder. Create a new directory named ```Custom-Themes``` in the ```Package``` directory (found under Preferences -> Browse Packages...). Move this tmTheme-file to the Custom-Themes folder.

Next, move the file ```LaTeX.sublime-settings``` to the ```Package/User``` directory. This settings file will specify to use the "Light LaTeX Scheme" as the default color scheme for LaTeX. Additionally it will center the text (without needing to use distraction-free mode!) and set the word wrap at 86 columns, and add some space between lines to improve readability.


_Happy LaTeXing!_