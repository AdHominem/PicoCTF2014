## **Problem Set**

We found a weird piece of paper with [this](https://picoctf.com/problem-static/crypto/ecc/ecc_handout.txt) written on it. I can't make heads or tails of it, but it seems to be talking about an encoded message. Can you get the message for us? 

## **Attempts**

I solve the equation for b which turns out to be `268892790095131465246420`. Now I need to decrypt the message. ECC cryptography works by creating an elliptic curve, an equation based on two integers a and b over a finite field of size n. I actually wonder why such a topic appears in a CTF aimed at high schoolers. Anyways, we have all variables we need including the message which is a point C and the private key which is d. I follow the hint and use [sagemath](https://cloud.sagemath.com/). 
See [this](http://www.johannes-bauer.com/compsci/ecc/) as a nice learning reference.


## **Solution**

Then I fire up sagemath, submitting the variables n, a and b first. Then I generate a new finite field with `F = FiniteField(n)` and a new elliptic curve by `C = EllipticCurve(F, [ a, b ])`. Then I chose a point `G = C.point((236857987845294655469221, 12418605208975891779391))` and multiply that point with d, resulting in `(6976767380847367326785 : 828669833265826932708578 : 1)`. When the two first coordinates are concatenated and submitted to the supplied python function, they return the flag `E L L I P T I C   C U R V E S   A R E   F U N`.
