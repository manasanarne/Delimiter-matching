# Delimiter-matching
#include<stdio.h>
#define MAX 20
char a[MAX];
int top=-1;
void push(char c)
{
    /*if(top==MAX-1)
    {
        printf("The stack is overflown\n");
    }
    else
    {*/
        a[++top]=c;
 
}
char pop()
{
    return a[top--];
}
void main()
{
    char expression[MAX],c,x;
    int flag=1,i=0;
    printf("Enter the expression for delimiter matching \n");
    scanf("%s",expression);
    while(expression[i]!='\0')
    {
        c=expression[i];
        if(c=='('||c=='['||c=='{')
        {
            push(c);
        }
        else if(c==')'||c==']'||c=='}')
        {
            if(top==-1)
            {
                flag=0;
                break;
            }
            else
            {
                x=pop();
                if((x=='('&&c==')')||(x=='['&&c==']')||(x=='{'&&c=='}'))
                {
                    flag=1;
                }
                else
                {
                    flag=0;
                    break;
                }
            }
        }
        i++;
    }
if(top!=-1)
{
    flag=0;
}
if(flag==1)
{
    printf("Matched");
}
else
{
    printf("Not mathced");
}
}


OUTPUT:
Enter the expression for delimiter matching
[{a+b}+c]}
Not mathced
