# breadth_first_srerch
#include<stdio.h>
#define SIZE 10
/* Queue Data Structure */
#define Q_SIZE 100
int Q[Q_SIZE];
int rear, front;
/* Graph Data Structure */
int G[SIZE][SIZE]; // To store Graph
int nov; // To store no. of Vertices
int noe; // To store no. of edges
int visited[SIZE];
void init_Q()
{
rear = -1;
front= -1;
}
int isFull()
{
if(rear == Q_SIZE - 1)
return 1;
else
return 0;
}
int isEmpty()
{
if(front == rear)
return 1;
else
return 0;
}
void addQ(int item)
{
if(isFull())
{
printf("Queue is Full !! \n");
}
else
{
rear++;
Q[rear] = item;
}
}
int delQ()
{
if( isEmpty())
{
return -1;
}
else
{
front++;
return Q[front];
}
}
void accept()
{
int i,j,k;
printf("How many Vertices : ");
scanf("%d", &nov);
printf("How many Edges : ");
scanf("%d", &noe);
for(k=1; k<=noe; k++)
{
printf("Enter Edge (Vi,Vj) : ");
scanf("%d %d", &i,&j);
G[i][j] = 1;
G[j][i] = 1; //remove this line in case of directed Graph
}
}
void display()
{
int i,j;
printf("\nAdjacency Matrix\n");
printf("------------------\n");
for(i=0; i<nov; i++)
{
for(j=0; j<nov; j++)
{
printf("%d ", G[i][j]);
}
printf("\n");
}
}
void bfs(int start)
{
int i,j;
printf("\nBFS : ");
addQ(start);
while(!isEmpty())
{
i = delQ();
if(visited[i]==0)
{
printf("%d ", i);
visited[i] = 1;
}
for( j=0; j<nov; j++)
{
if(G[i][j] == 1 && visited[j]==0)
{
addQ(j);
}
}
}
printf("\n");
}
int main()
{
int start;
accept();
display();
init_Q();
printf("\nEnter Starting Vertex : ");
scanf("%d", &start);
bfs(start);
}
ow many Vertices : 4
How many Edges : 5
Enter Edge (Vi,Vj) : 0 1
Enter Edge (Vi,Vj) : 1 3
Enter Edge (Vi,Vj) : 3 2
Enter Edge (Vi,Vj) : 2 0
Enter Edge (Vi,Vj) : 0 3
Adjacency Matrix
------------------
0 1 1 1 
1 0 0 1 
1 0 0 1 
1 1 1 0 
Enter Starting Vertex : 0
BFS [Start V0] : 0 1 2 3



