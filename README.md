# TIK-TAK-TOE


#include <stdio.h>

void printBoard(int b[3][3])
{
    for(int i=0;i<3;i++)
    {
        for(int j=0;j<3;j++)
        {
            if(b[i][j]>9)
            {
                printf("%c ",b[i][j]);
            }
            else
            {
                printf("%d ",b[i][j]);
            }
        }
        printf("\n");
    }
}

void insertBoard(int b[3][3],int inp,int t)
{
    for(int i=0;i<3;i++)
    {
        for(int j=0;j<3;j++)
        {
            if(b[i][j]==inp)
            {
                b[i][j]=t;
            }
        }
    }
}

int checkState(int b[3][3])
{
    for(int i=0;i<3;i++)
    {
        if(b[i][0]==b[i][1] && b[i][1]==b[i][2])
        {
            return 1;
        }
    }
    for(int i=0;i<3;i++)
    {
        if(b[0][i]==b[1][i] && b[1][i]==b[2][i])
        {
            return 1;
        }
    }
    if(b[0][0]==b[1][1] && b[1][1]==b[2][2])
    {
        return 1;
    }
    if(b[0][2]==b[1][1] && b[1][1]==b[2][0])
    {
        return 1;
    }
    int c=0;
    for(int i=0;i<3;i++)
    {
        for(int j=0;j<3;j++)
        {
            if(b[i][j]<10)
            {
                c++;
            }
        }
    }
    if(c==0)
    {
        return 2;
    }
    return 0;
}

int main()
{
    int board[3][3]={{0,1,2},{3,4,5},{6,7,8}};
    int player=1;
    int win=0;
    int input;
    int token;
    while(win!=1 && win!=2)
    {
        printBoard(board);
        if(player==1)
        {
            printf("player 1 enter:");
            token=88;
            player++;
        }
        else
        {
            printf("player 2 enter:");
            token=79;
            player--;
        }
        scanf("%d",&input);
        insertBoard(board,input,token);
        win=checkState(board);
    }
    if(win == 1)
    {
        if(player==2)
        {
            printf("player 1 won");
        }
        else
        {
            printf("player 2 won");
        }
    }
    else
    {
        printf("DRAW");
    }
    return 0;
}
