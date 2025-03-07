# Stego Gambit

Do you dare to accept the **Stego Gambit**? I know you can find the checkmate, but can you find the flag?

## Analyzing the Image

We received a chess-themed image as part of the **StegoChess** challenge. Unlike a regular image, this one requires us to follow the chess piece movements and map them to letters. The extracted hidden data revealed a password, indicating that additional hidden information might be present.

## Extracting Hidden Data

Using **steghide**, we can extract the flag from the image with the following command:

```bash
steghide extract -sf <path/to/file>
```

## Brute-Forcing the move

Since we are unsure about the exact move format or rotation, we use a brute-force method to generate possible all move :

```python
from itertools import product

first_moves = ["Be4", "Bf3", "Bg2", "Bh1", "be4", "bf3", "bg2", "bh1"]

fixed_moves = ["Kxa2", "Qd2+"]
fixed_moves_variants = [[move, move.lower()] for move in fixed_moves]

passwords = []
for first_move in first_moves:
    for variations in product(*fixed_moves_variants):
        password = f"{first_move}_{variations[0]}_{variations[1]}"
        passwords.append(password)

with open("passwords.txt", "w") as f:
    f.write("\n".join(passwords))
```

This method helps us generate multiple password possibilities to use with **steghide**.

## Flag

**Flag:** `KashiCTF{573g0_g4m617_4cc3p73d}`

---
A clever use of chess and steganography—checkmate!

