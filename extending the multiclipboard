#! /usr/bin/env python3
#mcb.pyw - saves and loads pieces of text to the clipboard.
#Usage:     ./mcb.pyw save <keyword> - saves clipboard to keyword
#           ./mcb.pyw <keyword> - loads keyword to clipboard
#           ./mcb.pyw list - loads all keywords to clipboard.

import shelve, pyperclip, sys

mcbShelf = shelve.open('mcb')

if len(sys.argv) == 3 and sys.argv[1].lower()== 'save':
    mcbShelf[sys.argv[2]] = pyperclip.paste()
    #shelf takes the third (second index) in the command line and assigns
    #what is on the clipboard to that keyword
elif len(sys.argv) == 2: #if there are only 2 arguments in the command line
    #list keywords and load content
    if sys.argv[1].lower() == 'list':
        pyperclip.copy(str(list(mcbShelf.keys())))
    elif sys.argv[1] in mcbShelf:
        pyperclip.copy(mcbShelf[sys.argv[1]])

#Extend the multiclipboard program in this so that it has a delet #<keyword> command line argument that will delete a keyword from the shelf.
#the code i have added to the code from the textbook, for the deletion of one keyword and its content, is as follows:
elif len(sys.argv) == 3 and sys.argv[1].lower()== 'delete' and sys.argv[2].lower() in mcbShelf.keys():
    del mcbShelf[sys.argv[2]]
#this is my attempt for the second part of the assignment but it is not correct?
elif len(sys.argv) == 2 and sys.argv[1]== 'DELETEALL':
    for i in list(mcbShelf.keys()):
        del mcbShelf[i]

mcbShelf.close()
