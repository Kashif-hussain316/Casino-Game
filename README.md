# Casino-Game
Building a feature casino game.
// Casino Royale

#include<stdio.h>
#include<stdlib.h>
#include<time.h>

int cash=100;
void Play(int bet)
{
	char c[3]={'J','K','Q'};
	
	printf("Shuffling Cards.......\n");
	srand(time(NULL));
	
	int i;
	for(i=0;i<5;i++)
	{
		int x= rand()%3;
		int y= rand()%3;
		
		int temp=c[x];
		c[x]=c[y];
		c[y]=temp;
	}
	
	int playerguess;
	printf("What is the Correct Position of the Queen: 1,2 or 3?\n");
	scanf("%d",&playerguess);
	
	if (c[playerguess-1]=='Q')
	{
		cash+=5*bet;
		printf("You Win!!! Result=\%c %c %c\" Total Cash=%d\n",c[0],c[1],c[2],cash);	
	}
	
	else
	{
		cash-=bet;
		printf("You Loose!!! Result=\%c %c %c\" Total Cash=%d\n",c[0],c[1],c[2],cash);
	}
}

int main()
{
	int bet;
	printf("Welcome to the Game\n\n");
	printf("Total Cash= $%d\n\n",cash);
	
	while(cash>0)
	{
		printf("Placed Your Bet: $");
		scanf("%d",&bet);
		
		if (bet==0 || bet>cash) break;
		Play(bet);
	}
}
