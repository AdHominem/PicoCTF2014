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
For each password character, the key is repeatedly xored with the character value times 2 plus 3. Since the highest charcater value you can produce in ASCII is '~' = 126, the highest possible xor value is 255. This also means that whatever key is eventually used, he is no longer than 255 aka one byte.

I write a script to brute force the encrypted file, comparing the result of each iteration with the standard wordlist to filter out gibberish results:

```python
import sys

input_data = open(sys.argv[1], 'r').read()
wordlist = open('/usr/share/dict/american-english', 'r').read()


def brute():
	for integer in range(256):
		result = xor(input_data, integer)
		for word in result.split(' '):
			if word != "" and word in wordlist:
				print(result + "\n")
				break


def xor(input_data, key):
    result = ""
    for ch in input_data:
        result += chr(ord(ch) ^ key)

    return result


brute()
```

Note that an easier solution would have been using Python's string.printable.

## **Solution**

Using my brute force script, the clear text message appears among the results. The flag is c79915c9dc408440dd00c9b317a68a
