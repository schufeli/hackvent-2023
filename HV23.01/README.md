# HV23.01 A letter from Santa

## Description

Finally, after 11 months of resting, Santa can finally send out his presents and challenges again. He was writing a letter to his youngest baby elf, who's just learning his **ABC/A-Z**'s. Can you help the elf read the message?

## Solution

Securing this flag turned into quite the puzzle-solving marathon. Navigating to the webpage and opting for the first dropdown element, I dropped in an `A`, revealing this intricate pattern.

![Pattern](assets/pattern.png)

After some pondering on the various dropdown patterns, I decided to take a hands-on approach. I sketched each pattern on paper, and what do you know – it shaped up into a QR code! The next step involved transferring it to Google Sheets, line by line. A few minutes later, the complete QR code emerged. Scanning it with my smartphone finally unveiled the coveted flag.

![QR-Code](assets/qr-code-sheet.png)

## Flag

```
HV23{qr_c0des_fun}
```