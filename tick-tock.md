## **Problem Set**
The file contains a program which basially just does modulo operations and displays a clock. I need to find a passwort and a signature which, when entered as parameters, should yield the flag

## **Attempts**

The one is pretty much math only.

## **Solution**

The wanted password must hold (password % m == r) for ALL tuples (r, m) in secretz

```python
secretz = [(1, 2), (2, 3), (8, 13), (4, 29), (130, 191), (343, 397), (652, 691), (858, 1009),
           (689, 2039), (1184, 4099), (2027, 7001), (5119, 10009), (15165, 19997), (15340, 30013),
           (29303, 70009), (42873, 160009), (158045, 200009)]
```

Also password^signature % (200009 * 160009) must be 1

I first split the tuples in moduli n and numbers a:
```python
n = [2, 3, 13, 29, 191, 397, 691, 1009, 2039, 4099, 7001, 10009, 19997, 30013, 70009, 160009, 200009]
a = [1, 2, 8, 4, 130, 343, 652, 858, 689, 1184, 2027, 5119, 15165, 15340, 29303, 42873, 158045]
```
...and use the Chinese Remainder Theorem to calculate the password:

`password = crypto.crt(n, a)`

Now I need to calculate the signature. This could be easy to solve if Euler's Formula can be applied:

`print(crypto.gcd(83359654581036155008716649031639683153293510843035531, 200009 * 160009))`

Result is one, so we can use Euler's Formula: a^phi(n) = 1 mod n
Since both 200009 and 160009 are prime, phi(n) is 200008 * 160008

signature = 32002880064

When both password and signature are entered, the flag was given.
