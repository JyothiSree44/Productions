# Productions
#include<stdio.h> 
#include<math.h> 
#include<string.h> 
#include<ctype.h> 
#include<stdlib.h> 
int n,m=0,i=0,j=0; 
char a[10][10],f[10]; 
void follow(char c); 
void refirst(char c);
void first(char c); 
int main()
{
int i,z; 
char c,ch; 
char name[20];
char rollno[15];
printf("enter the name:");
scanf("%s",name);
printf("enter roll no:");
scanf("%s",rollno); 
printf("\n Enter the no of prooductions:\n");
scanf("%d",&n);
printf("Enter the productions:\n"); 
for(i=0;i<n;i++) 
scanf("%s%c",a[i],&ch);
do
{ 
m=0;
printf("Enter the elemets whose fisrt & follow is to be found:"); 
scanf("%c",&c);
first(c); 
printf("First(%c)={",c); 
for(i=0;i<m;i++) 
printf("%c",f[i]);
printf("}\n");
strcpy(f," ");
//flushall(); 
m=0;
follow(c); 
printf("Follow(%c)={",c); 
for(i=0;i<m;i++) 
printf("%c",f[i]);
printf("}\n");
printf("Continue(0/1)?");
scanf("%d%c",&z,&ch);
}
while(z==1); 
return 0;
}
void refirst(char c)
{
int j; 
if(!(isupper(c)))
f[m++]=c; 
for(j=0;j<n;j++)
{
if(a[j][0]==c)
{
if(a[j][2]=='$') 
{
follow(a[j][0]);
}
else if(islower(a[j][2]))
f[m++]=a[j][2]; 
else 
refirst(a[j][2]);
}
}
}
void first(char c)
{
int j; 
if(!(isupper(c)))
f[m++]=c; 
for(j=0;j<n;j++)
{
if(a[j][0]==c)
{
if(a[j][2]=='$') 
{
f[m++]='$';
}
else if(islower(a[j][2]))
f[m++]=a[j][2]; 
else 
first(a[j][2]);
}
}
}
void follow(char c)
{ if(a[0][0]==c)
f[m++]='$';
for(i=0;i<n;i++)
{
for(j=2;j<strlen(a[i]);j++)
{
if(a[i][j]==c)
{
if(a[i][j+1]!='\0')
refirst(a[i][j+1]); 
if(a[i][j+1]=='\0' && c!=a[i][0]) 
follow(a[i][0]);
}
}
}
}
