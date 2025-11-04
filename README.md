# vegbiryani-eeltut4
#include <stdio.h>
#include <stdlib.h>  
#include <string.h>  

struct Veg_biryani {
    int bir_price;
    int bir_time;
    char bir_restaurant_name[50];
};

int compareByDeliveryTime(const void *a, const void *b) {
    struct Veg_biryani *bir1 = (struct Veg_biryani *)a;
    struct Veg_biryani *bir2 = (struct Veg_biryani *)b;
    return bir1->bir_time - bir2->bir_time;
}
int compareByprice(const void *a, const void *b) {
    struct Veg_biryani *bir1 = (struct Veg_biryani *)a;
    struct Veg_biryani *bir2 = (struct Veg_biryani *)b;
    return bir1->bir_price - bir2->bir_price;
}

int main() {
    printf("**** DISH NAME IS VEG BIRYANI*****\n");
struct Veg_biryani bir[5];
    int i;
    int C;

for (i = 0; i < 3; i++) {
        printf("\nEnter the name of the restaurant providing this dish: ");
        scanf("%s", bir[i].bir_restaurant_name); 
        printf("Enter the time required to deliver (in mins): ");
        scanf("%d", &bir[i].bir_time);
        printf("Enter the Price of the dish: ");
        scanf("%d", &bir[i].bir_price);
    }
    printf("                 \n");
printf("How do you want to sort the data?\n");
    printf("1. sort by price\n");
    printf("2. sort by time\n");
    printf("ENTER YOUR CHOICE\n");
    scanf("%d",&C);
     if (C == 1) {
 qsort(bir, 3, sizeof(struct Veg_biryani), compareByprice);
 printf("======================================================");
 printf("\nSorted list of Veg Biryani based on price:\n");
 printf("======================================================");
    } 
    else if (C == 2) {
        qsort(bir, 3, sizeof(struct Veg_biryani), compareByDeliveryTime);
 printf("======================================================");
printf("\nSorted list of Veg Biryani based on delivery time:\n");
 printf("======================================================");

    } 
    else {
        printf("\nInvalid choice!\n");
        return 1;
    }

    for (i = 0; i < 3; i++) {
        printf("\nRestaurant: %s", bir[i].bir_restaurant_name);
        printf("\nTime to deliver: %d mins", bir[i].bir_time);
        printf("\nPrice: %d\n", bir[i].bir_price);
    }


    return 0;
}
