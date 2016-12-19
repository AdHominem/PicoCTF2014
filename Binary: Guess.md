## **Problem Set**

This program requires you to guess a random 32-bit number! Sounds difficult, right? There is a server running at vuln2014.picoctf.com:4546, and the source can be found [here](https://picoctf.com/problem-static/binary/Guess/guess.c). 

## **Attempts**

A brief look at the source code reveals a glaring format string vulnerability. 

## **Solution**

When the program asks for my name, I enter a format string and make it print out the top of the stack. Trying a few variables after the '32' indicating the part where the char buffer for name is assigned, the flag `leak_the_seakret` is revealed.
