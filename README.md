# first-rep
#include <stdio.h>
#include <stdlib.h>

int insertion(int *a,int n,int count)
{
	int i,j;
	for(i=1;i<n;i++){
		j=i-1;count++;
		int item=a[i];
		while(j>=0 && a[j]>item)
		{
			count+=2;
			a[j+1]=a[j];
			j--;
		}
		a[j+1]=item;
	}
	return count;
}
int main()
{
	FILE *f1,*f2,*f3;
	f1=fopen("bestinsertion.txt","w");
	f2=fopen("avginsertion.txt","w");
	f3=fopen("worstinsertion.txt","w");
	int n,i;
	for(n=10;n<110;n=n+10)
	{
		int *a;
		a=(int *)malloc(n*sizeof(int));
		///b case
		for(i=0;i<n;i++)
		{
			a[i]=i;
		}
		int count=0;
		int res1=insertion(a,n,count);
		fprintf(f1,"%d %d\n",n,res1);
			///a case
		for(i=0;i<n;i++)
		{
			a[i]=rand()%100;
		}
		int count1=0;
		int res2=insertion(a,n,count1);
		fprintf(f2,"%d %d\n",n,res2);
	
		///worst case
		for(i=0;i<n;i++)
		{
			a[i]= n-i;
		}
		int count3=0;
		int res3=insertion(a,n,count3);
		fprintf(f3,"%d %d\n",n,res3);
	}
}
