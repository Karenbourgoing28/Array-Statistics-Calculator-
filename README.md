# Array-Statistics-Calculator-
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <ctype.h>
#include <time.h>

void print(int x[], int n);
void randomNumbers(int a[], int n);
double average(int a[], int n);
int max(int a[], int n);
int min(int a[], int n);
void sort(int a[], int n);
double median(int a [], int n);

int main()
{
   srand(time(NULL));
   int n = rand() % (20 - 12 + 1) + 12;
   int x[n];
   
   randomNumbers(x, n);
   printf("Karen Bourgoing - Project 4 \n \n");
   printf("Sample Size = %d \n \n", n);
   printf("Array Elements: \n");
   print(x, n);
   printf("Maximum = %d,  Minimum = %d \n \n", max(x, n), min(x,n));
   printf("Average = %.3f \n \n", average(x, n));
   sort(x, n);
   print(x, n);
   printf("Median = %.1f \n", median(x, n));
   printf("Karen Bourgoing - End of Project 4");
    return 0;
}

void print(int x[], int n)
{
    int i;
    for(i = 0; i < n; i++)
    {
        printf("%d ",x[i]);
    }
    printf("\n \n");
}

void randomNumbers(int a[], int n)
{
    int i;
    for(i=0; i < n; i++)
    {
        a[i] = rand() % (90 - 10 + 1) + 10;
    }
}

double average(int a[], int n)
{
    int s = 0;
    int i;
    for(i = 0; i < n; i++)
    {
        s += a[i];
    }
    
    return (double) s / n;
}

int max(int a[], int n)
{
    int m = a[0]; int i;
    for(i = 1; i < n; i++)
        if(a[i] > m)
            m = a[i];
    return m;
}

int min(int a[], int n)
{
    int m = a[0]; int i;
    for(i = 1; i < n; i++)
        if(a[i] < m)
            m = a[i];
    return m;
}

void sort(int a[], int n)
{
    int i;
    int j; 
    int m;
    int u;
    for (i = n - 1; i >= 0; i--)
    {
        m = i;
        for(j = i - 1; j >= 0; j--)
        {
            if(a[j] > a[m])
            {
                m = j;
            }
        }
        
        int t = a[i];
        a[i] = a [m];
        a[m] = t;
        
        for (u = 0; u < n; u++)
        {
            printf(" %d ", a[u]);
            if((u + 1) % n == 0)
            {
                printf("\n");
            }
        }
        j--;
        m--;
    }
}

double median(int a[], int n)
{
    sort (a, n);
    
    if(n % 2 ==0)
    {
        int m = n / 2;
        return (double) (a[m - 1] + a[m]) / 2;
    }
    else
    {
        int m = n / 2;
        return (double) a[m];
    }
}

   
