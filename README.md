# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```c
#include <stdio.h>
#include <string.h>

void hillCipher(char text[], int key[3][3]) {
    int len = strlen(text);

    // Convert to uppercase
    for (int i = 0; i < len; i++) {
        if (text[i] >= 'a' && text[i] <= 'z')
            text[i] -= 32;
    }

    // Make length multiple of 3 (pad with 'X')
    while (len % 3 != 0) {
        text[len++] = 'X';
        text[len] = '\0';
    }

    printf("\nEncrypted Text: ");

    for (int i = 0; i < len; i += 3) {
        int p[3];
        for (int j = 0; j < 3; j++)
            p[j] = text[i + j] - 'A';

        int c[3] = {0, 0, 0};
        for (int r = 0; r < 3; r++) {
            for (int k = 0; k < 3; k++) {
                c[r] += key[r][k] * p[k];
            }
            c[r] = c[r] % 26;  // modulo 26
        }

        for (int j = 0; j < 3; j++)
            printf("%c", c[j] + 'A');
    }
    printf("\n");
}

int main() {
    char text[100];
    int key[3][3];

    printf("Enter the plaintext: ");
    scanf("%s", text);

    printf("Enter the 3x3 key matrix (row-wise):\n");
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            scanf("%d", &key[i][j]);

    hillCipher(text, key);

    return 0;
}
```
## OUTPUT
<img width="1735" height="736" alt="Screenshot 2025-11-02 142305" src="https://github.com/user-attachments/assets/7d7e2d21-16b0-4c95-a35f-e552ce231abc" />

## RESULT
Thus, The C program to implement the hill cipher substitution techniques.
