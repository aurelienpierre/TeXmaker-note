TeXmaker-note
=============

A simple module to include manuscript notes in a LaTeX editor like TeXmaker

_______________________________________________________


TeXmaker-note is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.
                                                                         
This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details. You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/> 

_______________________________________________________

Aim of this programm
=
Taking notes with LaTeX, especially during science and maths lectures, can be very powerfull thanks to index and table of contents features. But it can be very long and tough when you want to render complicated graphics and figures on the fly. In this case, it can be a good idea to draw figures by hands, with graphical interfaces like graphic tablets or tablet pc.

But how to interface graphic devices with LaTeX in order to improve efficency during note-taking ?

In this purpose, I have written a cross-platform script in Python to interface manuscript note-taking and LaTeX code.

_______________________________________________________
Platforms
=
TeXmaker-note has been tested on Ubuntu Linux 12.04.

Written in Python, it is virtually compatible with Mac OS, Windows and all Linux/Unix distributions, as far as they are running a Python interpreter.
_______________________________________________________
Requirements
=
A LaTeX editor is strongly recommended, but not mandatory. I recommend TeXmaker, which is cross-platform and is one of the most "What You See Is What You Get" LaTeX editor. It allows the user to set highly customized macros and routines directly in the software. http://www.xm1math.net/texmaker/

The package PDFcrop is mandatory to crop figures before inserting them. It is provided by 'texlive-extra-utils' package on TeXlive distributions.

Xournal is mandatory to draw manuscript figures. It is a free and cross-platform software too, which supports advanced stylus features like eraser and pression sensibility. http://www.xm1math.net/texmaker/

And of course, this script requires a Python runtime. http://www.python.org/
_______________________________________________________
Installation
=
Put all the scripts provided in their archive in a convenient directory, such as "texmaker-note" directory somewhere in you personnal folder.

Then, give executions rights/permissions to all the scripts. In Linux/Unix, run the command :

  chmod -R 777 COMPLETE_PATH/texmaker-note
  
where COMPLETE_PATH is the absolute path of your directory beginning by '/' (e.g. /home/user)

Then, in TeXmaker, add a new user command with the command (In "User" menu) :

  COMPLETE_PATH/texmaker-note/texmaker-note.py

_______________________________________________________
Usage
=
Run the script 'texmaker-note.py' from TeXmaker user commands or from where you want (desktop lancher, shortcut, ...)

A Xournal window will open. Draw what you have to draw, then type 'Ctrl + E' to export your figure in PDF (it will be save automatically in the correct directory so don't change default saving directory), then 'Ctrl + S' and 'Ctrl + Q' to save and quit Xournal.

Now, the code '\includegraphics[scale=1]{img/img-1.pdf}' is stored in your clipboard, so you just have to copy it ('Ctrl + V') when you want in your .tex file to insert your figure.

Please notice that exporting to PDF is mandatory to include the graphics in a .tex document. The window display an A4-size document, but it will automatically be cropped before inserting (margin are deleted).

All PDF and xournal files are stored in an '/img' subdirectory of the current working directory (basically, the directory where your current .tex file is saved if you are running the script trough TeXmaker).

You don't have to manage the number of your images : the first hand-written image genereted is called 'img-1.pdf', and other are automatically called 'img-2.pdf' etc. The index number of the next image to be genereated is stored in an 'index' file saved in '/img' subdirectory, so the script can remember where it stopped last time, even if you have restart your computer.

_______________________________________________________
Ways to improve the script
=
For now, Xournal doesn't allow to save and export files directly from command line, the user has to do it himself and can only spare time by using shortcuts. In would be great to implement automatically saving and exporting while closing Xournal.

The hook placing the right code ('\includegraphics[scale=1]{img/img-1.pdf}') in the clipboard is also boring, but it is the only way I founded to keep the script cross-platform.
