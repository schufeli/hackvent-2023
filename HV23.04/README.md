# HV23.04 Bowser

## Description

Santa has heard that some kids appreciate a video game as a christmas gift. He would rather have the kids solve some CTF challenges, so he took some inspiration and turned it into a challenge. Can you save the princess?

## Solution

In the realm of CTF challenges, the more information we gather upfront, the quicker we can navigate without veering off course. Upon running the `File` command on the `bowser.elf` file, it revealed itself as a 64-bit ELF executable, dispelling any initial misdirection.

![File command output](assets/file-command.png)

### Loading the file into Ghidra

To delve deeper into the challenge, I opted to load the file into Ghidra for comprehensive research and decompilation. After some navigation, I pinpointed the main function housing an array with 73 elements.

A closer look at `line:91` unveiled a straightforward bitwise operation applied to extract flag characters. The task at hand became clear – reverse this operation to unveil the flag.

![Ghidra 1](assets/ghidra-1.png)
![Ghidra 2](assets/ghidra-2.png)

### Understanding the encryption
The encryption technique employed is a simple bitwise NOT operation, also known as bitwise complement or bitwise negation. This process entails applying the bitwise NOT (~) operator to each bit of the data being encrypted. In the realm of characters or bytes, this operation inverts the bits, transforming each 0 to 1 and vice versa.

### Crafting a Python script
With the realization that the flag can be retrieved by applying bitwise negation to the array, a concise Python script was crafted to unveil the flag:

```python
def decrypt_flag(encrypted_flag):
    decrypted_flag = []
    
    for char in encrypted_flag:
        decrypted_char = ~ord(char) & 0xFF
        decrypted_flag.append(chr(decrypted_char))

    return ''.join(decrypted_flag)

flag = [
    0xac, 0x90, 0x8d, 0x8d, 0x86, 0xd3, 0xdf, 0x86,
    0x90, 0x8a, 0x8d, 0xdf, 0x99, 0x93, 0x9e, 0x98,
    0xdf, 0x96, 0x8c, 0xdf, 0x96, 0x91, 0xdf, 0x9e,
    0x91, 0x90, 0x8b, 0x97, 0x9a, 0x8d, 0xdf, 0x9c,
    0x9e, 0x8c, 0x8b, 0x93, 0x9a, 0xd1, 0xff, 0xb7,
    0xa9, 0xcd, 0xcc, 0x84, 0xa6, 0x90, 0x8a, 0xa0,
    0xb7, 0x9e, 0x89, 0x9a, 0xa0, 0xac, 0x9e, 0x89,
    0x9a, 0x9b, 0xa0, 0x8b, 0x97, 0x9a, 0xa0, 0xaf,
    0x8d, 0x96, 0x91, 0x9c, 0x9a, 0x8c, 0x8c, 0x82
]

print(decrypt_flag(''.join([chr(value) for value in flag])))
```

In this Python script, the `decrypt_flag` function takes an encrypted flag as input (assumed to be a string), iterates through each character, and applies a series of bitwise operations to invert its bits. The result is then converted back to a character. The decrypted characters are stored in a list, and the final decrypted flag is obtained by joining these characters.

In the script's output, you'll observe the decrypted flag printed to the console.

![Python script output](assets/console-output.png)

## Flag

```
HV23{You_Have_Saved_the_Princess}
```