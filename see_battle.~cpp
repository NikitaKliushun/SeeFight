#include <vcl.h>
#pragma hdrstop
#pragma argsused
#include <conio.h>
#include <stdio.h>
#include <math.h>
#include <string.h>
#include <stdlib.h>
#include <iostream.h>
#include <clocale.h>

using namespace std;

char player1[10][10] = {
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'}
                        };

char for_player1[10][10] = {
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'}
                        };

char player2[10][10] = {
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'}
                        };

char for_player2[10][10] = {
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'},
                                          {'*','*','*','*','*','*','*','*','*','*'}
                        };

struct Ch
        {
                bool detSheep;
                int x1,y1,x2,y2,decks;
        } char_player1[10][10],char_player2[10][10];

bool make_sheep(char[10][10],struct Ch[10][10],int,int,int,int,int);
bool hitPlayer (char[10][10],char[10][10],struct Ch[10][10],int,int,int);
void input_sheeps(char [10][10],struct Ch[10][10]);
void make_field(char [10][10]);
void clean_field(char [10][10]);
int min (int,int);
int max (int,int);
void generate();
void reload_screen(char [10][10],char[10][10]);
void init();

int dx[8] = {-1,-1,-1,0,1,1,1,0}; int dy[8] = {-1,0,1,1,1,0,-1,-1}; int dx1[6] = {-1,0,1,0,-1,0}; int dy1[6] = {0,1,0,-1,0,1};
int sheepsNumberPlayer1 = 10, sheepsNumberPlayer2 = 10,  fixSheep = 10;
bool move = true, detSheep = false, detWay = false, detLast = false, detPlayer = false;
char detMenu;

void main ()
{
   SetConsoleCP(1251);
   SetConsoleOutputCP(1251);
   Check:
   init();
   printf("::::: МОРСКОЙ БОЙ (v 1.0) :::::\n\n1 - Играть с компьютером\n2 - Играть с Игроком №2\n0 - Выйти\n");
   scanf("%c",&detMenu);
   if (detMenu == '0') exit(0);
   if (detMenu == '1')
      {
        system("cls");
        input_sheeps(player1,char_player1);
        clean_field(player1);
        reload_screen(player1,for_player1);
        generate();
        clean_field(player2);
        while (sheepsNumberPlayer1 > 0 && sheepsNumberPlayer2 > 0)
        {
                int x,y,j,xx,yy,x1,y1;
                if (move)
                        {
                                Check1:
                                printf("\nВведите точку для нанесения удара (формат: '3 4')\n");
                                scanf("%d%d",&x1,&y1);
                                x1 = x1 - 1; y1 = y1 - 1;
                                if (x1 > -1 && x1 < 10 && y1 > -1 && y1 < 10 && for_player1[x1][y1] != '@' && for_player1[x1][y1] != '#')
                                {
                                        if ( hitPlayer(player2,for_player1,char_player2,x1,y1,2) == false ) move = false;
                                        else if (detLast) detLast = false;
                                }
                                else { printf("\nНекорректные данные! Попробуй ещё раз ...\n"); goto Check1; }

                        }
                else
                        {
                                Check3:
                                if (detSheep)
                                {
                                        if (fixSheep > sheepsNumberPlayer1) {detWay = false; detSheep = false; detLast = false; goto Check3; }
                                        if (detWay)
                                        {
                                                if ( hitPlayer(player1,for_player2,char_player1,x + dx1[j],y + dy1[j],1) == false)  { x == xx; y = yy; j = j + 2; move = true; }
                                                else { x = x + dx1[j]; y = y + dy1[j]; }
                                        }
                                        else
                                        {
                                               for (j = j++; j < 4; j++)
                                                        if (x + dx1[j] > -1 && x + dx1[j] < 10 && y + dy1[j] > -1 && y + dy1[j] < 10 && for_player2[x + dx1[j]][y + dy1[j]] != '@')
                                                            if ( hitPlayer(player1,for_player2,char_player1,x + dx1[j],y + dy1[j],1) ) { detWay = true; xx = x; yy = y; x = x + dx1[j]; y = y + dy1[j]; break; }
                                                            else { move = true; break; }
                                        }
                                }
                                else
                                {
                                        Check2:
                                        x = rand()%10; y = rand()%10;
                                        if (for_player2[x][y] != '@' && for_player2[x][y] != '#')
                                                if ( hitPlayer(player1,for_player2,char_player1,x,y,1) == false )  { move = true; detSheep = false; }
                                                else if (detLast == true) detLast = false;
                                                     else {detSheep = true; detWay = false; fixSheep = sheepsNumberPlayer1; j = -1; xx = x; yy = y; }
                                                else goto Check2;
                                }
                        }
                reload_screen(player1,for_player1);
        }
        if (sheepsNumberPlayer1 == 0) printf("\n::::: ПОРАЖЕНИЕ! :::::\n");
        else printf("\n::::::: ПОБЕДА! :::::::\n");
        system("pause");
        goto Check;
        /*Check4:
        printf("\n1 - Вернуться в меню\n0 - Выйти из игры\n");
        scanf("%c",detMenu);
        if (detMenu = 'y') goto Check;
        else if (detMenu = 'n') exit(0);
             else { printf("\nНекорректные данные! Попробуй ещё раз ...\n"); goto Check4; }*/
      }
   if (detMenu = '2')
      {
        system("cls");
        printf("::::: Игрок №1 :::::\n");
        input_sheeps(player1,char_player1);
        clean_field(player1);
        reload_screen(player1,for_player1);
        system("pause");
        system("cls");
        printf("::::: Игрок №2 :::::\n");
        input_sheeps(player2,char_player2);
        clean_field(player2);
        reload_screen(player2,for_player2);
        system("pause");
        while (sheepsNumberPlayer1 > 0 && sheepsNumberPlayer2 > 0)
        {
                int x,y,j,xx,yy,x1,y1;
                if (move)
                        {
                                Check5:
                                if (detPlayer == false) {
                                                                system("cls");
                                                                printf("::::: ХОД ИГРОКА №1 :::::\n\n");
                                                                system("pause");
                                                         }
                                reload_screen(player1,for_player1);
                                printf("\nВведите точку для нанесения удара (формат: '3 4')\n");
                                scanf("%d%d",&x1,&y1);
                                x1 = x1 - 1; y1 = y1 - 1;
                                if (x1 > -1 && x1 < 10 && y1 > -1 && y1 < 10 && for_player1[x1][y1] != '@' && for_player1[x1][y1] != '#')
                                {
                                        if ( hitPlayer(player2,for_player1,char_player2,x1,y1,2) == false ) { move = false; detPlayer = false; }
                                        else detPlayer = true;
                                }
                                else { printf("\nНекорректные данные! Попробуй ещё раз ...\n\n"); system("pause"); goto Check5; }
                                reload_screen(player1,for_player1);
                                if (detPlayer == false) system("pause");
                        }
                else {
                                Check6:
                                if (detPlayer == false) {
                                                                system("cls");
                                                                printf("::::: ХОД ИГРОКА №2 :::::\n\n");
                                                                system("pause");
                                                         }
                                reload_screen(player2,for_player2);
                                printf("\nВведите точку для нанесения удара (формат: '3 4')\n");
                                scanf("%d%d",&x1,&y1);
                                x1 = x1 - 1; y1 = y1 - 1;
                                if (x1 > -1 && x1 < 10 && y1 > -1 && y1 < 10 && for_player2[x1][y1] != '@' && for_player2[x1][y1] != '#')
                                {
                                        if ( hitPlayer(player1,for_player2,char_player1,x1,y1,1) == false ) { move = true; detPlayer = false; }
                                        else detPlayer = true;
                                }
                                else { printf("\nНекорректные данные! Попробуй ещё раз ...\n\n"); system("pause"); goto Check6; }
                                reload_screen(player2,for_player2);
                               if (detPlayer == false) system("pause");
                      }
        }
        if (sheepsNumberPlayer1 == 0) printf("\n::::: ПОБЕДИЛ ИГРОК №2! :::::\n");
        else printf("\n::::::: ПОБЕДИЛ ИГРОК №1! :::::::\n");
        system("pause");
        goto Check;
        /*Check7:
        printf("\n1 - Вернуться в меню\n0 - Выйти из игры\n");
        scanf("%c",detMenu);
        if (detMenu = 'y') goto Check;
        else if (detMenu = 'n') exit(0);
             else { printf("\nНекорректные данные! Попробуй ещё раз ...\n"); goto Check7; }   */
      }
}

void init()
{
        int i,j;
        for (i = 0; i < 10; i++)
                for (j = 0; j < 10; j++)
                {
                        player1[i][j] = player2[i][j] = for_player1[i][j] = for_player2[i][j] = '*';
                        char_player1[i][j].detSheep = char_player2[i][j].detSheep = false;
                        char_player1[i][j].decks = char_player2[i][j].decks = 0;
                }
        sheepsNumberPlayer1 = sheepsNumberPlayer2 = fixSheep = 10;
        move = true; detSheep = detWay = detLast = detPlayer = false;
}

void input_sheeps(char player[10][10],Ch char_player[10][10])
{
        int i,j,x1,x2,y1,y2; char _x1[100],_x2[100];
        char s;
        for (i = 0; i < 4; i++){
            for (j = 0; j < 4 - i; j++)
            {
                Check1:
                printf("\nВведите координаты крайних палуб (формат: '5 4 5 6')\n");
                scanf("%d%d",&x1,&y1);
                if (i > 0)
                        {
                                scanf("%d%d",&x2,&y2);
                        }
                else {x2 = x1; y2 = y1;}
//                x1 = (int)(_x1[0]) - 96; x2 = (int)(_x2[0]) - 96;
                if (x1 < 1 || x1 > 10 || y1 < 1 || y1 > 10
                   || x2 < 1 || x2 > 10 || y2 < 1 || y2 > 10
                   ||(x1 != x2 && y1 != y2) )
                   { printf("\nНекорректные данные! Попробуй ещё раз ...\n"); goto Check1; }
                if (x1 == x2) if ( fabs(y2 - y1) < i || fabs(y2 - y1) > i ) { printf("\nНекорректные данные! Попробуй ещё раз ...\n"); goto Check1; }
                if (y1 == y2) if ( fabs(x2 - x1) < i || fabs(x2 - x1) > i ) { printf("\nНекорректные данные! Попробуй ещё раз ...\n"); goto Check1; }
                if (make_sheep(player,char_player,x1,y1,x2,y2,i + 1) == false) { printf("\nНекорректные данные! Попробуй ещё раз ...\n"); goto Check1; };
                system("cls");
                make_field(player);
             }
        }
}

bool make_sheep (char player[10][10],Ch char_player[10][10],int x1, int y1, int x2, int y2, int decks)
{
        int i,j;
        if (x1 == x2)
           {
                for (i = min(y1,y2) - 1; i < max(y1,y2); i++ )
                    if (player[x1-1][i] != '@' && player[x1-1][i] != '#') {
                                                                                 player[x1-1][i] = '#';
                                                                                 char_player[x1-1][i].detSheep = true;
                                                                                 char_player[x1-1][i].x1 = x1-1;
                                                                                 char_player[x1-1][i].x2 = x2-1;
                                                                                 char_player[x1-1][i].y1 = y1-1;
                                                                                 char_player[x1-1][i].y2 = y2-1;
                                                                                 char_player[x1-1][i].decks = fabs(y2-y1)+1;
                                                                          }
                    else {
                          for (j = min(y1,y2) - 1; j < i; j++ )
                               if (player[x1-1][j] == '#') {
                                                                player[x1-1][j] = '*';
                                                                char_player[x1-1][j].detSheep = false;
                                                           }
                          return false;
                         }
               for (i = min(y1,y2) - 1; i < max(y1,y2); i++ )
                    for (j = 0; j < 8; j++)
                        if (x1 - 1 + dx[j] > -1 && x1 - 1 + dx[j] < 10 && i + dy[j] > -1 && i + dy[j] < 10
                            && player[x1 - 1 + dx[j]][i + dy[j]] != '#' ) player[x1 - 1 + dx[j]][i + dy[j]] = '@';
           }
        else if (y1 == y2)
                {
                        for (i = min(x1,x2) - 1; i < max(x1,x2); i++ )
                            if (player[i][y1-1] != '@' && player[i][y1-1] != '#') {
                                                                                        player[i][y1-1] = '#';
                                                                                        char_player[i][y1-1].detSheep = true;
                                                                                        char_player[i][y1-1].x1 = x1-1;
                                                                                        char_player[i][y1-1].x2 = x2-1;
                                                                                        char_player[i][y1-1].y1 = y1-1;
                                                                                        char_player[i][y1-1].y2 = y2-1;
                                                                                        char_player[i][y1-1].decks = fabs(x2-x1)+1;
                                                                                  }
                            else {
                                   for (j = min(x1,x2) - 1; j < i; j++ )
                                        if (player[j][y1-1] == '#') {
                                                                        player[j][y1-1] = '*';
                                                                        char_player[j][y1-1].detSheep = false;
                                                                    }
                                   return false;
                                 }
                        for (i = min(x1,x2) - 1; i < max(x1,x2); i++ )
                            for (j = 0; j < 8; j++)
                                if (i + dx[j] > -1 && i + dx[j] < 10 && y1 - 1 + dy[j] > -1 && y1 - 1 + dy[j] < 10
                                    && player[i + dx[j]][y1 - 1 + dy[j]] != '#' )player[i + dx[j]][y1 - 1 + dy[j]] = '@';

                }
}

int min (int x, int y)
{
        if (x < y) return x;
        else return y;
}

int max (int x, int y)
{
        if (x > y) return x;
        else return y;
}

void make_field (char player[10][10])
{
        int i,j; char k = 'a';
        printf("   1 2 3 4 5 6 7 8 9 10\n\n");
        for (i = 0; i < 10; i++) {
                printf("%c  ",k);
                for (j = 0; j <10; j++)
                     printf("%c ",player[i][j]);
                printf("\n"); k++;
        }
}

void generate ()
{
        int i,j,x1,x2,y1,y2;
        for (i = 0; i <= 1; i++){
            for (j = 0; j < 4 - i; j++)
            {
                Check1:
                x1 = 1 + rand()%9; y1 = 1 + rand()%9;
                if (i > 0) {
                            int z = rand()%1;
                            if (z == 0) { x2 = x1;
                                         z = rand()%1;
                                         if (z == 0) y2 = y1 - i;
                                         else y2 = y1 + i; }
                                       /*  CheckY:
                                         y2 = y1 - i + rand()%(2*i);
                                         if (fabs(y2 - y1) < i) goto CheckY; } */
                            else {y2 = y1;
                                  z = rand()%1;
                                  if (z == 0) x2 = x1 - i;
                                  else x2 = x1 + i; }
                                  /*CheckX:
                                  x2 = x1 - i + rand()%(2*i);
                                  if (fabs(x2 - x1) < i) goto CheckX; };*/
                           }
                else {x2 = x1; y2 = y1;}
                if (player2[x1][y1] == '@' || player2[x1][y1] == '#' ||
                    player2[x2][y2] == '@' || player2[x2][y2] == '#' ||
                    make_sheep(player2,char_player2,x1,y1,x2,y2,i + 1) == false) goto Check1;
//                make_field(player2);
             }
        }
        make_sheep(player2,char_player2,1,4,3,4,3);
        make_sheep(player2,char_player2,4,1,6,1,3);
        make_sheep(player2,char_player2,4,6,7,6,4);
//        make_field(player2);

/*        for (i = 0; i < 10; i++)
             for (j = 0; j < 10; j++){
                 if ()
             }   */
}

void reload_screen (char player[10][10],char for_player[10][10])
{
        system("cls");
        printf("   ::::: ТВОЁ ПОЛЕ ::::\n");
        make_field(player);
        printf("\n   ::::: ПРОТИВНИК ::::\n");
        make_field(for_player);
}

void clean_field (char player[10][10])
{
        int i,j;
        for (i = 0; i < 10; i++)
             for (j = 0; j < 10; j++)
                 if (player[i][j] == '@') player[i][j] = '*';
}
bool hitPlayer (char player[10][10],char for_player[10][10],Ch char_player[10][10],int x,int y,int sheepsNumber)
{
        int i,j,k,x1,y1,x2,y2,decks;/*,nextX,nextY,prevX,prevY; bool check,det;*/
        Check1:
/*        scanf("%d%d",&x,&y);
        x = x - 1; y = y - 1;
        if (x > -1 && x < 10 && y > -1 && y < 10
             && */
              if ( for_player[x][y] != '@' && for_player[x][y] != '#' )
            if (player[x][y] == '#')
                {
                        for_player[x][y] = '#';
                        player[x][y] = '@';
                        char_player[x][y].detSheep = false;
                        x1 = char_player[x][y].x1; x2 = char_player[x][y].x2; y1 = char_player[x][y].y1; y2 = char_player[x][y].y2; decks = char_player[x][y].decks;
                        for (i = min(char_player[x][y].x1,char_player[x][y].x2); i < max(char_player[x][y].x1,char_player[x][y].x2) + 1; i++)
                                for (j = min(char_player[x][y].y1,char_player[x][y].y2); j < max(char_player[x][y].y1,char_player[x][y].y2) + 1; j++)
                                        char_player[i][j].decks--;
                         if (char_player[x][y].decks == 0)
                                {
                                        if (sheepsNumber == 1) sheepsNumberPlayer1--;
                                        else sheepsNumberPlayer2--;
                                        detLast = true;
                                        for (i = min(char_player[x][y].x1,char_player[x][y].x2); i < max(char_player[x][y].x1,char_player[x][y].x2) + 1; i++)
                                                for (j = min(char_player[x][y].y1,char_player[x][y].y2); j < max(char_player[x][y].y1,char_player[x][y].y2) + 1; j++)
                                                {
                                                        char_player[i][j].detSheep = false;
                                                        for (k = 0; k < 8; k++)
                                                                if (i + dx[k] > -1 && i + dx[k] < 10 && j + dy[k] > -1 && j + dy[k] < 10 && for_player[i+dx[k]][j+dy[k]] != '#') { for_player[i+dx[k]][j+dy[k]] = '@'; player[i+dx[k]][j+dy[k]] = '@'; }
                                                }
                                }
                        /*check = true;
                        for (j = 0; j < 8; j++)
                             if (x + dx[j] > -1 && x + dx[j] < 10 && y + dy[j] > -1 && y + dy[j] < 10)
                                 if (player[x + dx[j]][y + dy[j]] == '#') { check = false; break; }
                        if (check) {
                                        if (sheepsNumber == 1) sheepsNumberPlayer1--;
                                        else  sheepsNumberPlayer2--;
                                        det = true; prevX = prevY = 100;
                                        while (det == true)
                                        {
                                               det = false;
                                               for (j = 0; j < 8; j++)
                                                    if (x + dx[j] > -1 && x + dx[j] < 10 && y + dy[j] > -1 && y + dy[j] < 10)
                                                       if (x + dx[j] != prevX || y + dy[j] != prevY)
                                                          if (for_player[x + dx[j]][y + dy[j]] == '#') { nextX = x + dx[j]; nextY = y + dy[j]; det = true; }
                                                          else for_player[x + dx[j]][y + dy[j]] = '@';
                                               prevX = x; prevY = y; x = nextX; y = nextY;
                                        }
                                 }
                       /* system("cls");
                        make_field(player1);
                        printf("\n");
                        make_field(for_player1); */
                        return true;
                }
            else
                {
                        for_player[x][y] = '@';
                        player[x][y] = '@';
                      /*  system("cls");
                        make_field(player1);
                        printf("\n");
                        make_field(for_player1); */
                        return false;
                }
        //else { printf("\nIncorrect value! Try again ...\n"); goto Check1; }
}


