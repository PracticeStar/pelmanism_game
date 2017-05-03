# pelmanism_game

#include<process.h>
#include<stdio.h>
#include<windows.h>
#include<time.h>
#include<stdlib.h>
char a[4][4],b[4][4]={'*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*'};
int i,j,x1,y1,x2,y2,r;
int fun(char a[4][4])
{
    int i,j;
    for(i=0;i<4;i++)
    for(j=0;j<4;j++)
         if(a[i][j]=='*')
    {
        return 1;break;
    }
}
void sz(char b[4][4])
{
    int i,j;
    for(i=0;i<4;i++)
     {
         for(j=0;j<4;j++)
        printf("%4c",b[i][j]);
    printf("\n");
     }
}
void zm()
{
    srand((unsigned)time(NULL));
    int k,c[8]={1,2,3,4,5,6,7,8},count[8]={0,0,0,0,0,0,0,0};
    for(i=0;i<4;i++)
        for(j=0;j<4;j++)
    {
        do{
            k=rand()%8+1;
            if(k==c[k-1])count[k-1]++;
        }while(count[k-1]>2);
        a[i][j]=c[k-1]+48;
    }
}
void main()
{
    zm();
    sz(a);
    Sleep(2000);
    system("cls");
    do
    {
        sz(b);
        printf("请输入两个坐标，坐标范围1~8,x1,y1,x2,y2:\n");
        scanf("%d%d%d%d",&x1,&y1,&x2,&y2);
        if(a[x1-1][y1-1]==a[x2-1][y2-1])
        {
            b[x1-1][y1-1]=a[x1-1][y1-1];
            b[x2-1][y2-1]=a[x2-1][y2-1];
        }
        else { for(i=0;i<4;i++)
        {
            for(j=0;j<4;j++)
            {
                if((i==(x1-1))&&(j==(y1-1)))
                    printf("%4c",a[i][j]);
                else if((i==(x2-1))&&(j==(y2-1)))
                    printf("%4c",a[i][j]);
                else
                printf("%4c",b[i][j]);
            }printf("\n");}
        }
        Sleep(2000);
        system("cls");
        r=fun(b);
    }while(r==1);
    printf("u win!\n");
}
