# TASK: tic-tac-toe game
## Easy: 
Ask user for row and column and write in the two dimensional array a value "1" in the correct place.

Check whether or not the row chosen by user contains all 1.

If all elements in row contain 1, then let player know they won.

### “*In case code part doesn`t open or show properly - I will copy it here also:*“
```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        // Initialize the board size and board
        final int n = 3;
        int[][] board = new int[n][n];

        // Initialize Scanner for player inputs
        Scanner in = new Scanner(System.in);
        System.out.println("Tic Tac Toe is ready for play!\n");
        System.out.print("What is your name, player 1? ");
        String p1 = in.nextLine();
        System.out.print("What is your name, player 2? ");
        String p2 = in.nextLine();

        boolean player1 = true;
        boolean gameEnded = false;

        // Main game loop
        while (!gameEnded) {
            drawBoard(board);
            System.out.println((player1 ? p1 : p2) + "'s Turn:");

            int row, col;
            while (true) {
                System.out.print("Enter a row number (0, 1, or 2): ");
                row = in.nextInt();
                System.out.print("Enter a column number (0, 1, or 2): ");
                col = in.nextInt();

                // Check for valid position
                if (isValidMove(board, row, col, n)) {
                    break;
                }
            }

            // Place the move on the board
            board[row][col] = 1;

            // Check for a winning row
            if (rowIsFull(board, row)) {
                drawBoard(board);
                System.out.println((player1 ? p1 : p2) + " has won!");
                gameEnded = true;
            } else {
                player1 = !player1;
            }
        }
        in.close();
    }

    // Function to draw the tic tac toe board
    public static void drawBoard(int[][] board) {
        System.out.println("Board:");
        for (int[] row : board) {
            for (int cell : row) {
                System.out.print(cell + " ");
            }
            System.out.println();
        }
    }

    // Function to check if all elements in the given row are 1
    public static boolean rowIsFull(int[][] board, int row) {
        for (int cell : board[row]) {
            if (cell != 1) {
                return false;
            }
        }
        return true;
    }

    // Function to validate the move
    public static boolean isValidMove(int[][] board, int row, int col, int n) {
        if (row < 0 || col < 0 || row >= n || col >= n) {
            System.out.println("This position is off the bounds of the board! Try again.");
            return false;
        } else if (board[row][col] != 0) {
            System.out.println("Someone has already made a move at this position! Try again.");
            return false;
        }
        return true;
    }
}
```

