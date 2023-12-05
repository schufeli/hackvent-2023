# HV23.03 Santa's grille

## Description

While contemplating the grille and turning some burgers, Santa decided to send all the hackers worldwide some season's greetings.

![Santas Grille](assets/grille.png)

## Solution

Upon conducting a Google image reverse search of the provided image in the challenge description, I discovered the concept of a grille cipher. Delving into the details, I perused the [Wikipedia article](https://en.wikipedia.org/wiki/Grille_(cryptography)) to grasp the intricacies of this cryptographic technique.

Armed with this newfound knowledge, I embarked on a trial-and-error exploration in GIMP. Recognizing that the plaintext should begin with `HV23{`, I initially overlooked the possibility of a counter-clockwise rotation. It dawned on me shortly afterward that the letter `m` also required encircling, simplifying the solution considerably.

![Grille in gimp 1](assets/grill-gimp-1.png)
![Grille in gimp 2](assets/grill-gimp-2.png)
![Grille in gimp 3](assets/grill-gimp-3.png)
![Grille in gimp 4](assets/grill-gimp-4.png)

## Flag

```
HV23{m3rry_h8ckvent2023}
```