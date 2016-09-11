## **Problem Set**

> Everyone loves the Tower of Hanoi puzzle. Well it appears the Toaster Bot wants you to play an essentially identical game called "Towers of Toast". The game doesn't seem to be working though... Can you win anyway? Perhaps by loading a winning saved game? Download the Java code [here](https://picoctf.com/problem-static/reversing/towers-of-toast/Main.java). 

## **Attempts**

1. Compiling and running the file it's clear the game is broken. But there is a utility to load save games. I inspect the source code.
2. The flag will be displayed if one of the poles has all of the disks.
3. If we manage to pu all disks on one pole, this will trigger the win condition. Since we can not play, we need to do this by loading a working savegame.
4. It seems the savegames are numbers representing the disks, each disk being one of the first 40 prime numbers. The disk prime numbers are recursively multiplied with each other to form the savegame number. That means an empty pole must have a savegame number of 1, while a full pole will be the factorial of the 40 primes.

## **Solution**

I inject a few lines into the code to make it display the factorial of the first 40 primes:

```java
		System.out.println(getPrimes(GAME_SIZE).stream().reduce(BigInteger::multiply).get());
```

Then I load a savegame, supplying 1 for the first two poles and the huge number yielded by my code and I get the flag 166589903787325219380851695350896256250980509594874862046961683989710.
