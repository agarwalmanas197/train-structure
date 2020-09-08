# A structure is a user defined data type in C. A structure creates a data type that can be used to group items of possibly different types into a single type.

### How to create a structure?
‘struct’ keyword is used to create a structure. Following is an example.

```
struct address 
{ 

   char name[50]; 

   char street[100]; 

   char city[50]; 

   char state[20]; 

   int pin; 
};
 ```
### How to declare structure variables?
A structure variable can either be declared with structure declaration or as a separate declaration like basic types.
```
// A variable declaration with structure declaration. 

struct Point 
{ 

   int x, y; 

} p1;  // The variable p1 is declared with 'Point' 

  

  
// A variable declaration like basic data types 

struct Point 
{ 

   int x, y; 
};  

  

int main() 
{ 

   struct Point p1;  // The variable p1 is declared like a normal variable 
}

How to initialize structure members?
Structure members cannot be initialized with declaration. For example the following C program fails in compilation.


struct Point 
{ 

   int x = 0;  // COMPILER ERROR:  cannot initialize members here 

   int y = 0;  // COMPILER ERROR:  cannot initialize members here 
};  
The reason for above error is simple, when a datatype is declared, no memory is allocated for it. Memory is allocated only when variables are created.

Structure members can be initialized using curly braces ‘{}’. For example, following is a valid initialization.


struct Point 
{ 

   int x, y; 
};  

  

int main() 
{ 

   // A valid initialization. member x gets value 0 and y 

   // gets value 1.  The order of declaration is followed. 

   struct Point p1 = {0, 1};  
}
 
How to access structure elements?
Structure members are accessed using dot (.) operator.

#include<stdio.h> 

  

struct Point 
{ 

   int x, y; 
}; 

  

int main() 
{ 

   struct Point p1 = {0, 1}; 

  

   // Accessing members of point p1 

   p1.x = 20; 

   printf ("x = %d, y = %d", p1.x, p1.y); 

  

   return 0; 
}
```
### Output:
```
x = 20, y = 1
```

### What is designated Initialization?

Designated Initialization allows structure members to be initialized in any order. This feature has been added in C99 standard.
```
#include<stdio.h> 

  

struct Point 
{ 

   int x, y, z; 
}; 

  

int main() 
{ 

   // Examples of initialization using designated initialization 

   struct Point p1 = {.y = 0, .z = 1, .x = 2}; 

   struct Point p2 = {.x = 20}; 

  

   printf ("x = %d, y = %d, z = %d\n", p1.x, p1.y, p1.z); 

   printf ("x = %d", p2.x); 

   return 0; 
} 
```

### Output:
```
x = 2, y = 0, z = 1
x = 20
```

#### Now, below is the desired program 

Define a structure data type TRAIN_INFO. The type contain Train No.: integer type Train name: string Departure Time: aggregate type TIME Arrival Time: aggregate type TIME Start station: string End station: string The structure type Time contains two integer members: hour and minute. Maintain a train timetable and implement the following operations: (i) List all the trains (sorted according to train number) that depart from a particular section. (ii) List all the trains that depart from a particular station at a particular time. (iii) List all he trains that depart from a particular station within the next one hour of a given time. (iv) List all the trains between a pair of start station and end station.
```
#include<stdio.h>
struct time
{
int hrs;
int min;
};
struct train_info
{
int tno;

char tna[30];
struct time dept;
struct time art;

char st[30],et[30];
}a[50];

int main()
{
int i,n,j,f=0,h,m,d=0;
char s[30],e[30];
printf("Enter number of trains\n");
scanf("%d/n",n);
for(i=0;i<n;i++)
{
printf("Enter train no/n Enter train name\n");
scanf("%d\n",a[i].tno);
gets(a[i].tna);
printf("Enter departure time in hrs and min\n");
scanf("%d%d\n",a[i].dept.hrs,a[i].dept.min);
printf("Enter arivial time in hrs and min\n");
scanf("%d%d\n",a[i].art.hrs,a[i].art.min);

printf("enter start and end station name\n");
gets(a[i].st);
gets(a[i].et);

}
//list of all the trains that depart 
// from a particular station
printf("enter start station\n");
gets(s);
for(i=0;i<n;i++)
{
f=0;
if(strlen(s)==strlen(a[i].st))
{
for(j = 0; j < strlen(s) ;j++)
 {
if(s[j]!=a[i].st[j+1])
{
f=1;
break;
}
}
}
if(f==0)
{
printf("\n%d %s",a[i].tno,a[i].tna);
printf("%d%d",a[i].dept.hrs,a[i].dept.min);
printf("%d%d\n",a[i].art.hrs,a[i].art.min);
 printf("%s%s",a[i].st,a[i].et);
}
}
//list of all the trains that depart 
// from a particular station
//at a particular time
printf("enter start station\n");
gets(s);
printf("/n Enter time");
scanf("%d%d/n",h,m);
for(i=0;i<n;i++)
{
f=0;
if((strlen(s)==strlen(a[i].st)) && a[i].dept.hrs==h && m==a[i].dept.min)
{
for(j = 0; j < strlen(s) ;j++)
 {
if(s[j]!=a[i].st[j+1])
{
f=1;
break;
}
}
}
if(f==0)
{
printf("\n%d %s",a[i].tno,a[i].tna);
printf("%d%d",a[i].dept.hrs,a[i].dept.min);
printf("%d%d",a[i].art.hrs,a[i].art.min);
 printf("%s%s",a[i].st,a[i].et);
}
}

//list of all the trains that depart 
// from a particular station
//with in 1hr from given time
printf("enter start station\n");
gets(s);
printf("/n Enter time");
scanf("%d%d/n",h,m);
for(i=0;i<n;i++)
{
f=0;
if((strlen(s)==strlen(a[i].st)) &&( (a[i].dept.hrs-h ==0 && a[i].dept.min - m<=59)||( a[i].dept.hrs-h==1 && a[i].dept.min-m==0) ) )
{
for(j = 0; j < strlen(s) ;j++)
 {
if(s[j]!=a[i].st[j+1])
{
f=1;
break;
}
}
}
if(f==0)
{
printf("\n%d %s",a[i].tno,a[i].tna);
printf("%d%d",a[i].dept.hrs,a[i].dept.min);
printf("%d%d",a[i].art.hrs,a[i].art.min);
 printf("%s%s",a[i].st,a[i].et);
}
}

//list of all the trains that depart 
// from a particular station
// and end at a particular station
printf("enter start and end station \n");
gets(s);
gets(e);
for(i=0;i<n;i++)
{
f=0;
d=0;
if(strlen(s)==strlen(a[i].st))
{
for(j = 0; j < strlen(s) ;j++)
 {
if(s[j]!=a[i].st[j+1])
{
f=1;
break;
}
}
}

if(strlen(e)==strlen(a[i].et))
{
for(j = 0; j < strlen(e) ;j++)
 {
if(e[j]!=a[i].et[j+1])
{
d=1;
break;
}
}
}



if(f==0&&d==0)
{
printf("\n%d %s",a[i].tno,a[i].tna);
printf("%d%d",a[i].dept.hrs,a[i].dept.min);
printf("%d%d\n",a[i].art.hrs,a[i].art.min);
 printf("%s%s",a[i].st,a[i].et);
}
}



    return 0;
}
```
