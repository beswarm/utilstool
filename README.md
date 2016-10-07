# utilstool
utils tools

#reading
1. sudo apt-get install texlive-latex-extra latex-xcolor texlive-latex-recommended
2. chmod a+x src2pdf;  bash src2pdf ;
3. enscript -r -2 --file-align=2 --highlight --line-numbers -o - `find . -name '*.java'` | ps2pdf - files.pdf
enscript is a program for converting text files to a variety of output formats; PostScript is the default, but you can also produce HTML, RTF, and a few others. The -r option says to print in landscape, -2 is two columns per page (save trees), --file-align=2 says that each new file should start on its own physical page, --highlight turns on language-specific syntax highlighting (it will try to figure out the language, or you can specify "java"), --line-numbers should be obvious, and -o - sends the output to standard-out (where it's piped to ps2pdf).

find generates the list of files; here I'm telling it to find all Java files under in the current directory. The output is passed as arguments to enscript; for "50-100 files" you should be OK, but you might need to read about xargs. You could get rid of the -name argument to generate a list of all files, or add multiple -name arguments to add more file types to the list; I wouldn't go with the "all files" approach, because then you'll get source-control files.

ps2pdf takes the PostScript output from enscript and converts it to PDF, which you can print.
