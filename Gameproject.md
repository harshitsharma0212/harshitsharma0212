Game: Labyrinth
Game Description:
Labyrinth is a console-based game where the player has to navigate through a maze to reach the treasure. The maze is represented by a 2D grid, and the player can move up, down, left, or right to reach the treasure.

Game Implementation:
Game Structure
We will use the following data structures and algorithms to implement the game:

Stack: to store the player's moves
Queue: to store the maze
2D Array: to represent the maze


#include <iostream>
#include <stack>
#include <queue>

using namespace std;

// Define the maze size
const int ROWS = 5;
const int COLS = 5;

// Define the maze
char maze[ROWS][COLS] = {
    {'S', '#', '#', '#', '#'},
    {'#', ' ', ' ', ' ', '#'},
    {'#', '#', '#', ' ', '#'},
    {'#', ' ', ' ', ' ', '#'},
    {'#', '#', '#', '#', 'T'}
};

// Function to print the maze
void printMaze() {
    for (int i = 0; i < ROWS; i++) {
        for (int j = 0; j < COLS; j++) {
            cout << maze[i][j] << " ";
        }
        cout << endl;
    }
}

// Function to check if the player has reached the treasure
bool hasReachedTreasure(int row, int col) {
    return maze[row][col] == 'T';
}

// Function to check if the move is valid
bool isValidMove(int row, int col) {
    return row >= 0 && row < ROWS && col >= 0 && col < COLS && maze[row][col] != '#';
}

// Function to play the game
void playGame() {
    int row = 0;
    int col = 0;
    stack<pair<int, int>> moves;

    while (true) {
        printMaze();
        cout << "Enter your move (U/D/L/R): ";
        char move;
        cin >> move;

        int newRow = row;
        int newCol = col;

        switch (move) {
            case 'U':
                newRow--;
                break;
            case 'D':
                newRow++;
                break;
            case 'L':
                newCol--;
                break;
            case 'R':
                newCol++;
                break;
            default:
                cout << "Invalid move. Please try again." << endl;
                continue;
        }

        if (isValidMove(newRow, newCol)) {
            moves.push({row, col});
            row = newRow;
            col = newCol;

            if (hasReachedTreasure(row, col)) {
                cout << "Congratulations! You have reached the treasure." << endl;
                break;
            }
        } else {
            cout << "Invalid move. Please try again." << endl;
        }
    }
}

int main() {
    playGame();
    return 0;
}
