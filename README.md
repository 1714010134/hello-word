# hello-word
just another repository
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
void menu();						
int input();				
void fence(); 		
void delete_stu();            
void Search_Name();    

int ser = 6;			
int people = 0;		
int scoree[100]; 	
char c;
	
int Find;		

long ID[20];
char name[20][10];
char sex[20][10];
char score[20][10];
int gong[20];
char dan[20][10];

char *name1[20];
char *sex1[20];
char *score1[20];
char *dan1[20];
char *q;

int main(int argc, char *argv[])
{
    int p;
for(p = 0;p < 20;p++)
{
    name1[p] = name[p];
    sex1[p] = sex[p];
    score1[p] = score[p];
    dan1[p] = dan[p];
    }

	while(ser != 0)
{		
	system("cls");			
	menu();			
	scanf("%d",&ser);
	if(ser == 1)
{	
		system("cls");			//清屏
		input();
	}
	else if(ser == 2){			//信息输出
		system("cls");			//清屏
		fence();
}
	else if(ser == 3)
{			//查找数据
		system("cls");			//清屏
        Search_Name();
	}
	else if(ser == 4)
{			//增加数据
		system("cls");			//清屏
        input();
	}
	else if(ser == 5)
{          //删除数据
        system("cls");
        delete_stu();
	}
}
    printf("程序结束！");
	return 0;
}

void menu(){				//显示菜单
	printf("\n");
	printf("\t\t---------------教师信息管理系统--------------\n");
	printf("\n");
	printf("\t\t\t\t1.输入教师信息\t\t\t\n");
	printf("\t\t\t\t2.显示教师信息\t\t\t\n");

	printf("\t\t\t\t3.查找教师信息\t\t\t\n");
	printf("\t\t\t\t4.增加教师信息\t\t\t\n");
	printf("\t\t\t\t5.删除教师信息\t\t\t\n");
    printf("\t\t\t\t0.退出系统\t\t\t\t\n");
	printf("\t\t---------------------------------------------\n");
	printf("\n\n请选择功能（0~5）：");
}

int input(){       
        int i;
		for(i = people;c != 'N';i++)
{
        printf("请输入教师号 姓名 性别 职称 工资 单位：\n例：20152132 张三 男 教授 8000 元\n");
		scanf("%d %s %s %s %d %s",&ID[i],name1[i],sex1[i],score1[i],&gong[i],dan1[i]);
		fflush(stdin);
		printf("继续Y 返回N\n");
		c=getchar();
       }
       c = 0;
       people = i;
}

void fence()
{      
	int j;

	printf("教师号\t姓名\t性别\t职称\t工资\t单位\n");

	for(j = 0;j < people;j++)
{
		printf("%d\t%s\t%s\t%s\t%d\t%s\n",ID[j],name1[j],sex1[j],score1[j],gong[j],dan1[j]);
	}
	fflush(stdin);
	printf("输出结束！（回车退出）");
  do{
  		c = getchar();
       }while(c!='\n');
       c = 0;
}

void Search_Name()
{    
    int i,j = 0;
char a[20];
while(c != 'N')
{
		printf("请输入要查找的名字：");
		fflush(stdin);
		gets(a);
		for(i = 0;i < people;i++){
		if(strcmp(a,name1[i]) == 0){
            j = 1;
            break;
		}
		}
		if(j == 1)
{
            printf("教师号\t姓名\t性别\t职称\t工资\t单位\n");
           printf("%d\t%s\t%s\t%s\t%d\t%s\n",ID[i],name1[i],sex1[i],score1[i],gong[i],dan1[i]);
		}
		else
            printf("\n用户不存在！\n");
        j = 0;
		printf("继续Y 返回N\n");
		c=getchar();
       }
       c = 0;
}

void delete_stu()
{     
    int i,j = 0,k,l;
    long int a[20];

	while(c != 'N')
{
		printf("请输入要删除的名字：");
		fflush(stdin);
		gets(a);
		for(i = 0;i < people;i++)
{
		if(strcmp(a,name1[i]) == 0)
{
            j = 1;
            break;
		}
		}
		if(j == 1)
{
           for(k = i;k < people;k++){
            ID[k] = ID[k+1];
            gong[k] = gong[k+1];
            q = sex1[k];
            sex1[k] = sex1[k+1];
            sex1[k+1] = q;
            q = score1[k];
            score1[k] = score1[k+1];
            score1[k+1] = q;
            q = dan1[k];
            dan1[k] = dan1[k+1];
            dan1[k+1] = q;
            q = name1[k];
            name1[k] = name1[k+1];
            name1[k+1] = q;
           }
        people--;
        printf("删除成功！");
		}
		else
            printf("\n用户不存在！");
        j = 0;
        fflush(stdin);
		printf("\n继续Y 返回N\n");
		c=getchar();
       }
       c = 0;
}
