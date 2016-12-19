## **Problem Set**

Can you change the secret? The binary can be found at /home/write_right/ on the shell server. The source can be found [here](https://picoctf.com/problem-static/binary/WriteRight/write_right.c). 

## **Attempts**

The source code tells me that I can use the program to overwrite a specific memory address. I need to change a secret value to make the comparison return true so it yields me the flag.

## **Solution**

Using objdump, I figure which address holds the secret value. The secret is in the source, so I just have to overwrite the address with the given bytes and I get the flag.
