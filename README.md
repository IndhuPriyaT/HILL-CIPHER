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
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int keymat[3][3] = {
    {17, 17, 5},
    {21, 18, 21},
    {2, 2, 19}
};

int invkeymat[3][3] = {
    {4, 9, 15},
    {15, 17, 6},
    {24, 0, 17}
};

void encode(char *ret, char a, char b, char c)
{
    int p1 = a - 'A';
    int p2 = b - 'A';
    int p3 = c - 'A';

    int x = p1 * keymat[0][0] + p2 * keymat[1][0] + p3 * keymat[2][0];
    int y = p1 * keymat[0][1] + p2 * keymat[1][1] + p3 * keymat[2][1];
    int z = p1 * keymat[0][2] + p2 * keymat[1][2] + p3 * keymat[2][2];

    ret[0] = (x % 26) + 'A';
    ret[1] = (y % 26) + 'A';
    ret[2] = (z % 26) + 'A';
    ret[3] = '\0';
}

void decode(char *ret, char a, char b, char c)
{
    int p1 = a - 'A';
    int p2 = b - 'A';
    int p3 = c - 'A';

    int x = p1 * invkeymat[0][0] + p2 * invkeymat[1][0] + p3 * invkeymat[2][0];
    int y = p1 * invkeymat[0][1] + p2 * invkeymat[1][1] + p3 * invkeymat[2][1];
    int z = p1 * invkeymat[0][2] + p2 * invkeymat[1][2] + p3 * invkeymat[2][2];

    ret[0] = ((x % 26 + 26) % 26) + 'A';
    ret[1] = ((y % 26 + 26) % 26) + 'A';
    ret[2] = ((z % 26 + 26) % 26) + 'A';
    ret[3] = '\0';
}

int main()
{
    char msg[100];
    char enc[100] = "";
    char dec[100] = "";
    char temp[4];

    printf("===== HILL CIPHER =====\n");

    printf("Enter Plain Text : ");
    scanf("%99s", msg);

    // Convert to uppercase
    for (int i = 0; msg[i] != '\0'; i++)
        msg[i] = toupper(msg[i]);

    // Padding with X
    while (strlen(msg) % 3 != 0)
        strcat(msg, "X");

    printf("\nPLAIN TEXT      : %s\n", msg);

    // Encryption
    for (int i = 0; i < strlen(msg); i += 3)
    {
        encode(temp, msg[i], msg[i + 1], msg[i + 2]);
        strcat(enc, temp);
    }

    printf("CIPHER TEXT     : %s\n", enc);

    // Decryption
    for (int i = 0; i < strlen(enc); i += 3)
    {
        decode(temp, enc[i], enc[i + 1], enc[i + 2]);
        strcat(dec, temp);
    }

    printf("DECRYPTED TEXT  : %s\n", dec);

    return 0;
}<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/9bd9ba8c-4c4b-46cf-92f1-116ce91edc3f" />

```

## OUTPUT

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/9bd9ba8c-4c4b-46cf-92f1-116ce91edc3f" />

## RESULT
Thus , to write a C program to implement the hill cipher substitution techniques is executed successfully.
