// Online C compiler to run C program online
#include <stdio.h>
#include<stdlib.h>
#include<time.h>
#include<unistd.h>
int n;  
// alloket function
void get_time();
void get_date();
void clear_screen();

int main() {
    // Write C code here
    char time[50],date[100];
    
     printf("entera chose  to printformet of time is:\n");
    printf(" 1. 24 hour \n");
    printf(" 2. 12 hour (default)\n");
    scanf("%d",&n);
   // for continusen ubdate
   while(1){
        get_time(time,n);
        get_date(date);
        clear_screen();
        printf("crrent time is: %s\n",time);
        printf("crrent date  is: %s ",date);
        sleep(1);// sleep for 1 secound;
    }
     return 0;
}
// creeate a  function 
// to get time
void get_time(char* buffer,int n){
     // creat variable;
     time_tm raw_time; 
     
    struct tm *current_time;
   
    
    
    time(&raw_time);
    current_time = localtime(&raw_time);
// 24 hour formet
    if(n == 1){
        strftime(buffer, 50,"%H:%M:%S ",current_time);
    }
// 12 hour formet
    else{
        strftime(buffer, 50,"%I:%M:%S %p",current_time);
    }
}
// to get date
void get_date(char* buffer){
     // creat variable;
     time_t raw_time;
     
    struct tm *current_time;
   
    
    
    time(&raw_time);
    current_time = localtime(&raw_time);
    
        strftime(buffer, 50,"%d %A %B  %Y ",current_time);
    
}
// for clear screen on a secound
void clear_screen(){
    #ifdef _WIN32
        system("cls");
    #else
        system("clear");
    #endif
}
