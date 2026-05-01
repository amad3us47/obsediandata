
```c
#include<stdio.h>
int main()
{
   int a,b;
   scanf("%d %d",&a,&b);

   int temp;
   temp=a;
   a=b;
   b=temp;

   printf("Value of a is %d\n",a);
   printf("Value of b is %d",b);
   return 0;
}
```