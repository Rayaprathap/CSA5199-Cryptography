#include <stdio.h>
#include <string.h>


void createPlayfairMatrix(char matrix[5][5]) {
    char key[] = "MFH IJKUNOPQZVWXYELARGBCD";
    int k = 0;

    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            matrix[i][j] = key[k++];
        }
    }
}


void preprocessMessage(const char* input, char* message) {
    int len = strlen(input);
    int j = 0;

    for (int i = 0; i < len; i++) {
        char ch = input[i];
        if (ch >= 'A' && ch <= 'Z') {
            message[j++] = ch;
        }
    }
    message[j] = '\0';
}


void encryptPlayfair(char matrix[5][5], const char* message, char* ciphertext) {
    int len = strlen(message);
    int p = 0;

    for (int i = 0; i < len; i += 2) {
        char firstLetter = message[i];
        char secondLetter = (i + 1 < len) ? message[i + 1] : 'X';

        int row1, col1, row2, col2;

        
        for (int row = 0; row < 5; row++) {
            for (int col = 0; col < 5; col++) {
                if (matrix[row][col] == firstLetter) {
                    row1 = row;
                    col1 = col;
                }
                if (matrix[row][col] == secondLetter) {
                    row2 = row;
                    col2 = col;
                }
            }
        }

        if (row1 == row2) {
            ciphertext[p++] = matrix[row1][(col1 + 1) % 5];
            ciphertext[p++] = matrix[row2][(col2 + 1) % 5];
        } else if (col1 == col2) {
            ciphertext[p++] = matrix[(row1 + 1) % 5][col1];
            ciphertext[p++] = matrix[(row2 + 1) % 5][col2];
        } else {
            ciphertext[p++] = matrix[row1][col2];
            ciphertext[p++] = matrix[row2][col1];
        }
    }

    ciphertext[p] = '\0';
}

int main() {
    char matrix[5][5];
    createPlayfairMatrix(matrix);

    const char* message = "Must see you over Cadogan West. Coming at once.";
    char cleanedMessage[500];
    char ciphertext[500];

    preprocessMessage(message, cleanedMessage);
    encryptPlayfair(matrix, cleanedMessage, ciphertext);

    printf("Encrypted Message: %s\n", ciphertext);

    return 0;
}
