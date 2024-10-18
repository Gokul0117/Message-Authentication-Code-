# EX-NO 13 Message Authentication Code 

## AIM:
To write a program to implement Message Authentication Code (MAC). 
## ALGORITHM:
STEP-1: Input the plaintext message and symmetric key. STEP-2: Input the MAC value. STEP-3: Perform XOR encryption
STEP-4: Display the encrypted message
STEP-5: Perform XOR decryption
STEP-6: Display the decrypted message
## PROGRAM :
```c
#include <stdio.h>
#include <string.h>

#define MAX_LEN 256 


void encrypt(const char *input, const char *key, char *output) {
    int len = strlen(input);
    int key_len = strlen(key);
    for (int i = 0; i < len; i++) {
        output[i] = input[i] ^ key[i % key_len]; 
    }
    output[len] = '\0'; 
}


void decrypt(const char *input, const char *key, char *output, int len) {
    int key_len = strlen(key);
    for (int i = 0; i < len; i++) {
        output[i] = input[i] ^ key[i % key_len]; 
    }
    output[len] = '\0'; 
}

int main() {
    char message[MAX_LEN];    
    char key[MAX_LEN];        
    char input_mac[3];       
    char encrypted[MAX_LEN];  
    char decrypted[MAX_LEN];  

    printf("\n **Simulation of MAC Algorithm**\n\n");
    printf(" DEVELOPED BY : GOKUL J\n");
    printf(" REG NO : 212222230038\n\n");

    printf("Enter the plaintext message: ");
    fgets(message, MAX_LEN, stdin);
    message[strcspn(message, "\n")] = 0;

    printf("Enter the symmetric key: ");
    fgets(key, MAX_LEN, stdin);
    key[strcspn(key, "\n")] = 0; 

    printf("Enter the MAC value (in hex format): ");
    scanf("%2s", input_mac); 

    encrypt(message, key, encrypted);
    int encrypted_length = strlen(message);

    printf("Encrypted message (raw bytes): ");
    for (int i = 0; i < encrypted_length; i++) {
        printf("%02x ", (unsigned char)encrypted[i]);
    }
    printf("\n");

    decrypt(encrypted, key, decrypted, encrypted_length); 
    printf("Decrypted message: %s\n", decrypted);

    return 0;
}




```

## OUTPUT :
![image](https://github.com/user-attachments/assets/627d66d0-ec25-46aa-9e40-e504194c216e)


## RESULT :
Thus the Message Authentication Code (MAC) had been implemented sucessfully.
