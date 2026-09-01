**EX. NO: 4: IMPLEMENTATION OF VIGENERE CIPHER**

**Name:** Shrenidhi

**Reg No:** 212223040196

**Dept:** CSE

**AIM:**

To implement the Vigenere Cipher substitution technique using a C program.

**DESCRIPTION:**

The Vigenere Cipher is a substitution cipher that uses a table of alphabets called the **Tabula Recta**, **Vigenere Square**, or **Vigenere Table**.

The table consists of the alphabet written 26 times in different rows. Each row is shifted cyclically to the left compared to the previous row, representing the 26 possible Caesar Ciphers.

During encryption, a repeating keyword is used. Each letter of the plaintext is encrypted using the corresponding letter of the keyword. The keyword is repeated until it matches the length of the plaintext.

For each plaintext character, the corresponding key character determines the shift value. The encrypted character is obtained by shifting the plaintext character according to the corresponding keyword character.

**ALGORITHM:**

**STEP 1:** Arrange the alphabets in rows and columns of a 26 × 26 matrix.

**STEP 2:** Shift the alphabets cyclically in each row to construct the Vigenere table.

**STEP 3:** Repeat the process for all 26 rows to construct the complete key matrix.

**STEP 4:** Read the keyword and plaintext.

**STEP 5:** Repeat the characters of the keyword sequentially until they match the length of the plaintext.

**STEP 6:** Take the corresponding letters of the plaintext and keyword.

**STEP 7:** Apply the Vigenere Cipher encryption formula to generate the cipher character.

**STEP 8:** Repeat the process for all characters to generate the complete cipher text.

**PROGRAM:**

```c id="vf8zqw"
#include <stdio.h>
#include <string.h>

// Function to perform Vigenere encryption
void vigenereEncrypt(char *text, const char *key)
{
    int textLen = strlen(text);
    int keyLen = strlen(key);

    for (int i = 0; i < textLen; i++)
    {
        char c = text[i];

        if (c >= 'A' && c <= 'Z')
        {
            text[i] = ((c - 'A' + (key[i % keyLen] - 'A')) % 26) + 'A';
        }
        else if (c >= 'a' && c <= 'z')
        {
            text[i] = ((c - 'a' + (key[i % keyLen] - 'A')) % 26) + 'a';
        }
    }
}

// Function to perform Vigenere decryption
void vigenereDecrypt(char *text, const char *key)
{
    int textLen = strlen(text);
    int keyLen = strlen(key);

    for (int i = 0; i < textLen; i++)
    {
        char c = text[i];

        if (c >= 'A' && c <= 'Z')
        {
            text[i] = ((c - 'A' - (key[i % keyLen] - 'A') + 26) % 26) + 'A';
        }
        else if (c >= 'a' && c <= 'z')
        {
            text[i] = ((c - 'a' - (key[i % keyLen] - 'A') + 26) % 26) + 'a';
        }
    }
}

int main()
{
    char message[] = "SECURITYLABORATORY";
    const char *key = "KEY";

    printf("Input Message      : %s\n", message);

    vigenereEncrypt(message, key);
    printf("Encrypted Message  : %s\n", message);

    vigenereDecrypt(message, key);
    printf("Decrypted Message  : %s\n", message);

    return 0;
}
```

**OUTPUT:**

<img width="544" height="410" alt="image" src="https://github.com/user-attachments/assets/b82f1e8d-a7ec-4ced-8b92-a17e167e72cd" />

**RESULT:**

The Vigenere Cipher program was successfully implemented using C. The plaintext was encrypted using the given keyword and successfully decrypted back to the original message.
