# Memory-Cards-game
A common memory matching game played by young children is to start with a deck of cards that contains identical pairs. For example, given six cards in the deck, two might be labeled “1,” two might be labeled “2,” and two might be labeled “3.” The cards are shuffled and placed face down on the table. The player then selects two cards that are face down, turns them face up, and if they match they are left face up. If the two cards do not match, they are returned to their original position face down. The game continues in this fashion until all cards are face up. Write a program that plays the memory matching game. Use 16 cards that are laid out in a 4 X 4 square and are labeled with pairs of numbers from 1 to 8. Your program should allow the player to specify the cards that she would like to select through a coordinate system.
// Course:  CS213 - Programming II  - 2018
// Title:   Assignment I - Task 3
// Purpose: Playing common matching game
// Author:  Eng.Seif Mostafa

#include<iostream>
#include<cstdlib>
#include<ctime>
using namespace std;
void hide() /// After face down we should hide the board
{
    _sleep(4000);
    for(int i=0 ; i<25 ; i++)
        cout<<endl;
}


int main(){
srand(time(0));



int cards[4][4];
///Fill All Elements of Matrix = 0
int Num[8]={1,2,3,4,5,6,7,8};
 for (int r=0; r<4; r++){
   for (int c=0; c<4; c++){
       cards[r][c]=0;
   }
   }
///Fill board by random numbers
for(int i=0;i<8;i++){
    for(int j=0;j<2;j++){
        int m,n;
        m=rand()%4;
        n=rand()%4;
        while(cards[m][n]!=0){
        m=rand()%4;
        n=rand()%4;
        }
        cards[m][n]=Num[i];

    }
}
///Design view of Player
cout<<"                                        Welcome To Memory Cards game";

cout<<"\n  1 2 3 4\n  -------\n";
for (int r=0; r<4; r++){
         cout<<r+1<<"|";
   for (int c=0; c<4; c++){
    cout<<"*"<<"  ";
   }
   cout<<endl;
   }
///Make Matrix to End the game in While Loop
int matrix [4][4];
for (int r=0; r<4; r++){
   for (int c=0; c<4; c++){
    matrix[r][c]=1;
   }
   }
///2-D Array of Stars to Represent in The Screen through While Loop
char ar[4][4]= {'*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*'};
///While Loop to player enter rows and col. of two cards
while(matrix[0][0]==1||matrix[0][1]==1||matrix[0][2]==1||matrix[0][3]==1||matrix[1][0]==1||matrix[1][1]==1||matrix[1][2]==1||matrix[1][3]==1||matrix[2][0]==1||matrix[2][1]==1||matrix[2][2]==1||matrix[2][3]==1||matrix[3][0]==1||matrix[3][1]==1||matrix[3][2]==1||matrix[3][3]==1){

int x,y,a,b;
cout<<"Choose dimesomins of first card: ";
cin>>x>>y;

cout<<"Choose dimesomins of second card: ";
cin>>a>>b;
///If player choose same dimensions
while(x==a && y==b){
    cout<<endl<<"Error! You Choose same rows and columns"<<endl;
    cout<<"Choose another rows and columns"<<endl;
cout<<"Enter dimensions of first card: ";
cin>>x>>y;
cout<< endl;
cout<<"Enter dimesomins of second card: ";
cin>>a>>b;



}

hide();
hide();
--x;
--y;
--a;
--b;
cout<<"\n  1 2 3 4\n  -------\n";
for (int r=0; r<4; r++){
     cout<<r+1<<"|";
   for (int c=0; c<4; c++){
    if(r==x&&c==y){
        cout<<cards[r][c]<<" ";
    }
    else if(r==a&&c==b){
        cout<<cards[r][c]<<" ";
    }
   else{
    cout<<ar[r][c]<<" ";
   }

   }
   cout<<endl;
   }
   if (cards[x][y]==cards[a][b]){
    matrix[x][y]=0;
    matrix[a][b]=0;
   ar[x][y]=char(cards[x][y]+'0');
   ar[a][b]=char(cards[a][b]+'0');
   }

}
}
