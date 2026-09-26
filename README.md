#include <stdio.h>

typedef struct
{
int rollNo;
char name[50];
float c, java, db;
float total, average;
char grade;
} Student;

int main()
{
Student s[50];
int n = 0;
int choice, i;
int roll, found;

do  
{  
    printf("\n===== STUDENT MANAGEMENT SYSTEM =====\n");  
    printf("1. Add Student\n");  
    printf("2. Display Students\n");  
    printf("3. Search Student\n");  
    printf("4. Exit\n");  

    printf("Enter choice: ");  
    scanf("%d", &choice);  

    if (choice == 1)  
    {  
        if (n == 50)  
        {  
            printf("\nStudent limit reached!\n");  
        }  
        else  
        {  
            printf("\nEnter Roll No: ");  
            scanf("%d", &s[n].rollNo);  

            printf("Enter Name: ");  
            scanf(" %[^\n]", s[n].name);  

            printf("\nEnter marks:\n");  

            printf("C     : ");  
            scanf("%f", &s[n].c);  

            printf("Java  : ");  
            scanf("%f", &s[n].java);  

            printf("DB    : ");  
            scanf("%f", &s[n].db);  

            /* Calculate total and average */  
            s[n].total = s[n].c + s[n].java + s[n].db;  
            s[n].average = s[n].total / 3;  

            /* Determine grade */  
            if (s[n].average >= 90)  
                s[n].grade = 'A';  
            else if (s[n].average >= 75)  
                s[n].grade = 'B';  
            else if (s[n].average >= 60)  
                s[n].grade = 'C';  
            else if (s[n].average >= 50)  
                s[n].grade = 'D';  
            else  
                s[n].grade = 'F';  

            n++;  

            printf("\nStudent added successfully!\n");  
        }  
    }  

    else if (choice == 2)  
    {  
        if (n == 0)  
        {  
            printf("\nNo student records found.\n");  
        }  
        else  
        {  
            printf("\nRoll No\tName\t\tTotal\tAverage\tGrade\n");  
            printf("--------------------------------------------------------\n");  

            for (i = 0; i < n; i++)  
            {  
                printf("%d\t%-15s %.2f\t%.2f\t%c\n",  
                       s[i].rollNo,  
                       s[i].name,  
                       s[i].total,  
                       s[i].average,  
                       s[i].grade);  
            }  
        }  
    }  

    else if (choice == 3)  
    {  
        printf("\nEnter Roll No: ");  
        scanf("%d", &roll);  

        found = 0;  

        for (i = 0; i < n; i++)  
        {  
            if (s[i].rollNo == roll)  
            {  
                printf("\nStudent Found!\n");  
                printf("Roll No : %d\n", s[i].rollNo);  
                printf("Name    : %s\n", s[i].name);  
                printf("C       : %.2f\n", s[i].c);  
                printf("Java    : %.2f\n", s[i].java);  
                printf("DB      : %.2f\n", s[i].db);  
                printf("Total   : %.2f\n", s[i].total);  
                printf("Average : %.2f\n", s[i].average);  
                printf("Grade   : %c\n", s[i].grade);  

                found = 1;  
                break;  
            }  
        }  

        if (found == 0)  
        {  
            printf("\nStudent not found!\n");  
        }  
    }  

    else if (choice == 4)  
    {  
        printf("\nExiting...\n");  
    }  

    else  
    {  
        printf("\nInvalid choice!\n");  
    }  

} while (choice != 4);  

return 0;

}
