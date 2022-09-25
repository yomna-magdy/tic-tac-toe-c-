#include<iostream>
using namespace std;




void drowBoard(char matrix[3][3]) {
    //system("cls");
    for (int i = 0; i < 3; i++)
    {
        for (int j = 0; j < 3; j++)
        {
            cout << " | " << matrix[i][j];
        }
        cout << " | \n -------------\n";
    }
}




char checkwinner(char matrix[3][3])
{

    int check_drow = 0;

    for (int i = 0; i < 3; i++)
    {
        int x_counter = 0, o_counter = 0;


        for (int j = 0; j < 3; j++)
        {
            if (matrix[i][j] <= '9' && matrix[i][j] >= '0')
                check_drow++;

            if (matrix[i][j] == 'X')
                x_counter++;
            else if (matrix[i][j] == 'O')
                o_counter++;
        }
        if (x_counter == 3 || o_counter == 3)
        {

            (o_counter > x_counter) ? cout << " winner is player ( O ) " : cout << " winner is player ( X ) ";
            return 0;
        }
    }

    for (int i = 0; i < 3; i++)
    {
        int x_counter = 0, o_counter = 0;

        for (int j = 0; j < 3; j++)
        {
            if (matrix[j][i] == 'X')
                x_counter++;
            else if (matrix[j][i] == 'O')
                o_counter++;
        }
        if (x_counter == 3 || o_counter == 3)
        {

            (o_counter > x_counter) ? cout << " winner is player ( O ) " : cout << " winner is player ( X ) ";
            return 0;
        }
    }

    int x_counter = 0, o_counter = 0;
    for (int i = 0; i < 3; i++)
    {
        for (int j = 0; j < 3; j++)
        {
            if (i == j || i + j == 2)

            {
                if (matrix[j][i] == 'X')
                    x_counter++;
                else if (matrix[j][i] == 'O')
                    o_counter++;
            }
            if (x_counter == 3 || o_counter == 3)
            {
                (o_counter > x_counter) ? cout << " winner is player ( O ) " : cout << " winner is player ( X ) ";
                return 0;
            }
        }



    }


    if (check_drow == 0)   return 'N';
    return '.';
}




void play(char matrix[3][3])
{

    char player = 'x';
    char position;
    
    pos:
    
    cout << "choose Position - player ( " << player << " ) : ";   cin >> position;
    for (int i = 0; i < 3; i++)
    {
        for (int j = 0; j < 3; j++)
        {   
            if (matrix[i][j] == position)
            {
                matrix[i][j] = player;
            }
            else
            {
                cout << "Invalid choice ... Please Try Again : \n";
                goto pos;
            }
        }
    }
    if (player == 'x')
    {
        player = 'o';
    }
    else
    {
        player = 'x';
    }

}


int main() {

start:

    char matrix[3][3] = { '1' , '2' , '3' ,  '4' , '5' ,'6' ,  '7' , '8' , '9' };






    while (checkwinner(matrix) == '.')
    {
        drowBoard(matrix);
        play(matrix);
    }

    if (checkwinner(matrix) == 'N')
        cout << "\n draw\n";
    else
        cout << checkwinner(matrix) << "\n\n";

    cout << "\nDo you want to play another game?  ... Yes / No? \n ";
    string answer;  cin >> answer;
    if (answer[0] == 'y' || answer[0] == 'Y')
        goto start;
    else
        return 0;

}
