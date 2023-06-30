# C-p34-3-
C语言学习笔记 p34 指针详解(3)
#include<stdio.h>
int main()
{
    //字符指针
    char ch='w';
    char* p=7ch;
    const char* p2="abcdef";
    //指针数组-数组-存放指针的数组
    int* arr[10];
    char* ch[5];
    //数组指针
    //int*p3;-整形指针-指向整形的指针
    //char* p4；-字符1指针-指向字符的指针
    int arr2[5];//数组
    int(*pa)[5]=&arr2;//取出数组的地址-数组指针
    return 0;
}


//数组参数、指针参数
//一维数组传参
void test(int arr[])//这种可行
void test(int arr[10])//这种可行
void test(int* arr)//可行
void test2(int* arr[20])//可以
void test2(int** arr)//可以
int main()
{
    int arr[10]={0};
    int* arr2[20]={0};
    test(arr);
    test2(arr);
    return 0;
}


void test(int arr[][5])
{
}//可省略行不可省略列
int main()
{
    int arr[3][5]={0};
    test(arr);//二维数组传参
    return 0;
}


void test1(int (*arr)[5])
{
}//这个传参就没问题，因为二维数组第一个元素是一个数组
int main()
{
    test1();
    return 0;
}

//一级指针传参
//传指针就拿指针类型接收

//二级指针传参
//也是传什么类型拿什么类型接收
void test(int** p)
{
}
int main()
{
    int* arr[10];
    test(arr);//指针数组传参也可以
    return 0;
}


//函数指针-指向函数的指针-用来存放函数地址
int Add(int x,int y)
{
    int z=0;
    z=x+y;
    return z;
}
int main()
{
    int a=10;
    int b=20;
    int arr[10]={0};
    int (*p)[10]=&arr;
    printf("%d\n",Add(a,b));
//以下输出都是一样，&函数名和函数名都是函数的地址，一模一样的
    printf("%p\n",&Add);
    printf("%p\n",Add);
//函数传参就是和数组传参一样只不过把数组指针换成了函数指针
    int(*pa)(int int)=Add;
    int (*pa)(2,3)=Add;
    printf("%d\n",(*pa)(2,3));
    return 0;
}


void Print(char*str)
{
    printf("%s\n",str);
}
itn main()
{
    void (*p)(char*)=Print;
    (*p)("hello bit");
    return 0;
}
