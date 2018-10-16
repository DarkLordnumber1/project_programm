# project_programm
#include<stdio.h>
#include<stdlib.h>
#include<stdbool.h>
int Index_First_Negative(int array[],int size);
int Index_Last_Negative(int array[],int size);
int Prod_InRange_NegativeP(int array[],int size);
int Prod_OutRange_NegativeP(int array[],int size);

int main(){
        int arr[100],arr_size=0,option;
        scanf("%d",&option);
        while(getchar()!='\n'){
                scanf("%d",&arr[arr_size]);
                        arr_size++;}
        switch(option){
            case 0:printf("%d\n",Index_First_Negative(arr,arr_size));
                   break;
            case 1:printf("%d\n",Index_Last_Negative(arr,arr_size));
                   break;
            case 2:printf("%d\n",Prod_InRange_NegativeP(arr,arr_size));    
                   break;
            case 3:printf("%d\n",Prod_OutRange_NegativeP(arr,arr_size));
                   break;
            default:printf("Данные некорректны\n");}
        return 0;
}
int Index_First_Negative(int array[],int size){
    int i;
    bool f=false;
    for(i=0;i<size;i++)
        if(array[i]<0){
        f=true;
        break;}
    if(!f)
        return -1;
    else
        return i;
}
int Index_Last_Negative(int array[],int size){
    int i;
    bool f=false;
    for(i=size-1;i>=0;i--)
        if(array[i]<0){
            if(!f)
            f=true;
            break;}
        if(f)
            return i;
        else
            return -1;
}
int Prod_InRange_NegativeP(int array[],int size){
    int i,first_negative,last_negative=-1,prod=1;
    first_negative=Index_First_Negative(array,size);
    for(i=size-1;i>first_negative;i--)
        if(array[i]<0){
            last_negative=i;
            break;}
        if((first_negative!=-1)&&(last_negative!=-1)){
            for(i=first_negative;i<last_negative;i++)
                prod*=(array[i]);
                return prod;}
        else    
            return -1;}
int Prod_OutRange_NegativeP(int array[],int size){
    int i,first_negative,last_negative,prod=1;
    first_negative=Index_First_Negative(array,size);
    for(i=size-1;i>first_negative;i--)
        if(array[i]<0){
            last_negative=i;
            break;}
        // if((first_negative!=0)||(last_negative!=(size-1))){
            for(i=0;i<first_negative;i++)
                        prod*=(array[i]);
            for(i=last_negative;i<size;i++)
                        prod*=(array[i]);
            return prod;
        // else return -1;}
        }
