
# HV23.09 Passage encryption

## Description

Santa looked at the network logs of his machine and noticed that one of the elves browsed a weird website. He managed to get the pcap of it, and it seems as though there is some sensitive information in there?!

## Solution

Firstly, as in other CTFs I extracted all files with wireshark and had a look at the downloaded HTML file which clearly states `Thank you for telling me your secrets!`. After a short look I decided to add all the numbers of the door pngs together with which i got the number: `2239869409783327322206976224099369`.

I tried getting some sense out of it so converting it to hex and then wanting a text out of it was the right approach. But not today my friends.. the output was `no flag2c�|)`.

So i began browsing wireshark again after what felt like an eternity and I slowly got frustrated. Something catched my attention. 

The HTTP requests to the endpoint `/?door=` have a different source port everytime. So I began writing them down which lead to the following list:

```
56772, 56786, 56750, 56751, 56823, 56776, 56811, 56748, 56807, 56749, 56810, 56803, 56795, 56802, 56811, 56814, 56795, 56812, 56811, 56814, 56816, 56753, 56795, 56810, 56811, 56755, 56795, 56800, 56811, 56748, 56814, 56736, 56825
```

After a closer look I realized that the number 56 can be stripped of every number and what remains brings us closer to the flag.

So i started investigating the pattern and soon realised that every time there is a 7 at the beginning it can be ignored and every time there is an 8 it equals to a 1. Now i wrote down the decimals into a list again:

```
72 86 50 51 123 76 111 48 107 49 110 103 95 102 111 114 95  112 111 114 116 53  95 110 111 55 95 100 111 48  114 36 125
```

Which revealed the flag to us in ASCII.

## Flag

```
HV23{Lo0k1ng_for_port5_no7_do0r$}
```



