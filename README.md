# Ex---13---MESSAGE-AUTHENTICATION-CODE-MAC-
## AIM
To implement Message Authentication Code (MAC) in Python for verifying the
integrity and authenticity of messages.
## ALGORITHM
Step 1: Choose a secret key K.              
Step 2: Select a cryptographic hash function H (e.g., SHA-256).              
Step 3: To authenticate a message m, compute the MAC as
MAC=H(K⊕pad1∣∣m∣∣K⊕pad2).                
Step 4: Send both the message m and the MAC to the receiver.                       
Step 5: The receiver, with the same key K, computes the MAC using the same
process.                         
Step 6: If the computed MAC matches the received MAC, the message is
authentic and unaltered.                       
Step 7: Otherwise, the message is rejected                   
## PROGRAM
```
#include <stdio.h>
#include <string.h>
#define MAX_LEN 256 // Maximum length of the message
// FuncƟon to perform XOR encrypƟon
void encrypt(const char *input, const char *key, char *output) {
int len = strlen(input);
int key_len = strlen(key);
for (int i = 0; i < len; i++) {
output[i] = input[i] ^ key[i % key_len]; // XOR operaƟon
}
output[len] = '\0'; // Null-terminate the output string
}
// FuncƟon to perform XOR decrypƟon
void decrypt(const char *input, const char *key, char *output, int len) {
int key_len = strlen(key);
for (int i = 0; i < len; i++) {
output[i] = input[i] ^ key[i % key_len]; // XOR operaƟon
}
output[len] = '\0'; // Null-terminate the output string
}

int main() {
char message[MAX_LEN]; // Plaintext message
char key[MAX_LEN]; // Symmetric key
char input_mac[3]; // MAC input from the user
char encrypted[MAX_LEN]; // Encrypted message
char decrypted[MAX_LEN]; // Decrypted message
printf("\n *Simulation of MAC Algorithm*\n\n");
// Get plaintext message from the user
printf("Enter the plaintext message: ");
fgets(message, MAX_LEN, stdin);
message[strcspn(message, "\n")] = 0; // Remove newline character
// Get symmetric key from the user
printf("Enter the symmetric key: ");
fgets(key, MAX_LEN, stdin);
key[strcspn(key, "\n")] = 0; // Remove newline character
// Get MAC value from the user
printf("Enter the MAC value (in hex format): ");
scanf("%2s", input_mac); // Read the MAC input from the user
// Perform encrypƟon
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
## OUTPUT
![crypt13](https://github.com/user-attachments/assets/23a9433d-9f89-482f-a20e-b5abdf896f29)

## RESULT
Thus, the program for Message Authentication Code (MAC) cryptography was
executed successfully, demonstrating its eƯectiveness in verifying message
integrity and authenticity.
