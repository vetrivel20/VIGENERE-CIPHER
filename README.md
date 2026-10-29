# VIGENERE-CIPHER

### Name:M.Vetrivel
### Register Number:212225040487
### Date:29-10-2026

## EX. NO: 4
 

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void encryption(char PT[], char key[], char CT[])
{
    int i, j = 0;
    int len = strlen(PT);
    int klen = strlen(key);

    for (i = 0; i < len; i++)
    {
        if (isalpha((unsigned char)PT[i]))
        {
            CT[i] = ((PT[i] - 'A' + key[j % klen] - 'A') % 26) + 'A';
            j++;
        }
        else
        {
            CT[i] = PT[i];
        }
    }

    CT[len] = '\0';
}

void decryption(char CT[], char key[], char DT[])
{
    int i, j = 0;
    int len = strlen(CT);
    int klen = strlen(key);

    for (i = 0; i < len; i++)
    {
        if (isalpha((unsigned char)CT[i]))
        {
            DT[i] = ((CT[i] - 'A' - (key[j % klen] - 'A') + 26) % 26) + 'A';
            j++;
        }
        else
        {
            DT[i] = CT[i];
        }
    }

    DT[len] = '\0';
}

int main()
{
    char PT[100], key[100], CT[100], DT[100];
    int i;

    printf("Enter the plaintext: ");
    scanf("%99s", PT);

    printf("Enter the key: ");
    scanf("%99s", key);

    for (i = 0; PT[i] != '\0'; i++)
        PT[i] = toupper((unsigned char)PT[i]);

    for (i = 0; key[i] != '\0'; i++)
        key[i] = toupper((unsigned char)key[i]);

    encryption(PT, key, CT);
    printf("Encrypted text: %s\n", CT);

    decryption(CT, key, DT);
    printf("Decrypted text: %s\n", DT);

    return 0;
}
```

## OUTPUT
![alt text](OUTPUT.png)

## RESULT
The implementation of Vigenere Cipher substitution technique using C program is executed sucessfully.