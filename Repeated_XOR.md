## **Problem Set**

There's a secret passcode hidden in the robot's "history of cryptography" module. But it's encrypted! Here it is, hex-encoded: [encrypted.txt](https://picoctf.com/api/autogen/serve/encrypted.txt?static=false&pid=82a42d1d859d5c2140e8942848e5db0e). Can you find the hidden passcode? 

## **Attempts**

Since this is a multi byte XOR, we need to find out the length of the key so we can separate the ciphertext into segments and brute force these individually. How do we get the length? Well, we can in theory use Hamming weight to determine that but I want to guess first.

## **Solution**
