#include <stdio.h>

#define MAX_ROWS 1000
#define MAX_COLS 1000

// Function to find the maximum consecutive black cells in a row
int maxConsecutiveRow(char matrix[MAX_ROWS][MAX_COLS], int row, int col) {
    int maxCount = 0;
    int count = 0;

    for (int j = 0; j < col; j++) {
        if (matrix[row][j] == '#') {
            count++;
            if (count > maxCount) {
                maxCount = count;
            }
        } else {
            count = 0;
        }
    }

    return maxCount;
}

// Function to find the maximum consecutive black cells in a column
int maxConsecutiveCol(char matrix[MAX_ROWS][MAX_COLS], int row, int col) {
    int maxCount = 0;
    int count = 0;

    for (int i = 0; i < row; i++) {
        if (matrix[i][col] == '#') {
            count++;
            if (count > maxCount) {
                maxCount = count;
            }
        } else {
            count = 0;
        }
    }

    return maxCount;
}

int main() {
    int t;
    scanf("%d", &t);

    while (t--) {
        int row, col;
        scanf("%d %d", &row, &col);

        // Input the matrix
        char matrix[MAX_ROWS][MAX_COLS];
        for (int i = 0; i < row; i++) {
            for (int j = 0; j < col; j++) {
                scanf(" %c", &matrix[i][j]);
            }
        }

        // Find the maximum consecutive black cells in each row and column
        int maxBorder = 0;
        for (int i = 0; i < row; i++) {
            int rowMax = maxConsecutiveRow(matrix, i, col);
            if (rowMax > maxBorder) {
                maxBorder = rowMax;
            }
        }

        for (int j = 0; j < col; j++) {
            int colMax = maxConsecutiveCol(matrix, row, j);
            if (colMax > maxBorder) {
                maxBorder = colMax;
            }
        }

        // Output the result for each test case
        printf("%d\n", maxBorder);
    }

    return 0;
}
