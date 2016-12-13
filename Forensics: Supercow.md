## **Problem Set**
Daedalus Corp. has a special utility for printing .cow files at /home/daedalus/supercow. Can you figure out how to get it to print out the flag? 

## **Attempts**
The supercow program has a setgid and can open .cow files only. Since the flag.txt has no read permission, I need to use supercow to open it for me.
I can not change the file name nor copy it, so I will use a symlink to virtually change the name.

## **Solution**
I return to my home dir and create a symlink to the flag.txt file, but named flag.cow. I can open this one with supercow and it grants the flag
`cows_drive_mooooving_vans`
