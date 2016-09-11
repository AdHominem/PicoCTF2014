## **Problem Set**

I am given both an encrypted file and the crypto program written in Python.

## **Attempts**

After browsing the code it becomes clear that the encrypt function has a flaw:

```python
def encrypt(input_data, password):
    key = 0
    for ch in password:
        key ^= ((2 * ord(ch) + 3) & 0xff)

    return xor(input_data, key)
```

The key is repeatedly xored, but its size remains the same.

I think about brute forcing the key. Using sys.getsizeof(), it seems the size of key is 24B, which seems too large.

It turns out that Python just stores integers as objects, yielding a larger memory allocation. The values themselves tho remain in the usual range, that is 8b for an integer. That is just 256 possible keys! 

I write a script to brute force the encrypted file, comparing the result of each iteration with the standard wordlist to filter out gibberish results.

## **Solution**

Using my brute force script, the clear text message appears among the results. The flag is c79915c9dc408440dd00c9b317a68a
