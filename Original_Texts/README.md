# File Extraction, Cleaning, and Manipulation

## English
"A Doll's House" by Ibsen was downloaded from Project Gutenberg in November of 2017

## Danish
"Et dukkehjem" by Ibsen, basic text, first edition, was downloaded from Universitetet i Oslo, Henrik Ibsens Skrifter, https://www.ibsen.uio.no/DRVIT_Du%7CDu79.xhtml?facs=Ja; February 26, 2019

## Textual cleaning and preparation
While the version of "A Doll's House" downloaded from Project Gutenberg in 2017 was already parsible through code, the Danish edition, downloaded from the University of Oslo was not. Extensive amounts of both programatic and manual cleaning occurred to get "Et dukkehjem" ready for processing. While the English edition exported with newlines between each new character speech, the Danish edition exported as one large chunk of text. Within that chunk, elements of the online fascimile remained, including facsimile page numbers as well as occasional declarations indicating the name of the script as well as the author. Newlines were added manually. While this would be possible to do using code, doing it manually enabled me to learn more about the language and the structure present in the Danish edition. Happily, just as with the English, the stage directions existed within parentheses, allowing the code that parses the English edition to be repurposed for the Danish one.
