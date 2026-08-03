# 3-BMultithreading---distance-between-planets-aestroids
#include <stdio.h>
#include <unistd.h>
#include <pthread.h>
#include <sys/wait.h>
void * task(void * arg){
    if(getppid() != 1)
        printf("Distance between Sun & Sirius = 8.6 light yrs\n");
    return NULL;}
int main () {
    pthread_t t;
    if(fork() == 0){
        pthread_create(&t, NULL, task, NULL);
        pthread_join(t, NULL);}
    else {
        printf("Distance b/w Earth & mars = 25 million km");
        wait(NULL);
        printf("All distance calculations completed.");}
    return 0;}
//Output
Distance b/w Earth & mars = 25 million km
Distance between Sun & Sirius = 8.6 light yrs
All distance calculations completed.
//
