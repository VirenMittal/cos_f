#include<stdio.h>
#include<windows.h>
#define pi 3.14159265359//defining a permanent variable whose value cant be changed
#define ABS(x) (((x) >= 0) ? x : -x)
float cosine(float x){
    float sum=0,i=0,t=1;
    while(ABS(t)>=1.0e-15){
    sum+=t;
    t*=(-1)*x*x/((2*i+1)*(2*i+2));
    i++;}
    return sum;
}
int main(){  
float a,x,sum1;
printf("Enter the value of x in degrees=");
scanf("%f",&a);
LARGE_INTEGER start, end, frequency;
long long cpu_time_used;
QueryPerformanceFrequency(&frequency);
QueryPerformanceCounter(&start);
x=(a/180)*pi;//converting degree to radian
sum1=cosine(x);
    printf("\nvalue of cos x is %f",sum1);
     QueryPerformanceCounter(&end);
    cpu_time_used = (end.QuadPart - start.QuadPart) * 1e9 / frequency.QuadPart;
    printf("\nCPU Time used: %lld nanoseconds\n", cpu_time_used);
return 0;
}
