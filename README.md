# polynomial
#include <stdio.h>
#include<stdlib.h>
struct node
{
    int coeff;
    int expo;
    struct node* next;
}*newnode,*temp,*temp1,*temp2,*temp3;
struct node* head=NULL;
struct node* tail=NULL;
struct node* create(struct node* head)
{
    int ch;
    int c,e;
    do
    {
        newnode=(struct node*)malloc(sizeof(struct node));
        printf("Enter the coefficient value to insert in a single linked list:\n");
        scanf("%d",&c);
        printf("Enter the exponentiation value to insert in a single linked list:\n");
        scanf("%d",&e);
        newnode->coeff=c;
        newnode->expo=e;
        newnode->next=NULL;
        if(head==NULL)
        {
            head=newnode;
            tail=newnode;
        }
        else
        {
            tail->next=newnode;
            tail=newnode;
        }
        printf("Enter 1 to continue:\n");
        fflush(stdin);
        scanf("%d",&ch);
    }while(ch==1);
    return head;
}
void display(struct node* head)
{
    printf("\nThe created polynomial is:\n");
    temp=head;
    while(temp!=NULL)
    {
        printf("+%dx^%d",temp->coeff,temp->expo);
        temp=temp->next;
    }
}
void add_polynomial(struct node *head1,struct node *head2)
{
    printf("\nThe addition polynomial is:\n");
    temp1=head1;
    temp2=head2;
    while(temp1&&temp2)
    {
        if(temp1->expo==temp2->expo)
        {
            printf("+%dx^%d",temp1->coeff+temp2->coeff,temp1->expo);
            temp1=temp1->next;
            temp2=temp2->next;
        }
        else if(temp1->expo<temp2->expo)
        {
            printf("%dx^%d",temp2->coeff,temp2->expo);
            temp2=temp2->next;
        }
        else
        {
            printf("%dx^%d",temp1->coeff,temp1->expo);
            temp1=temp1->next;
        }
    }
    if(temp1==NULL)
    {
        while(temp2!=NULL)
        {
            printf("%dx^%d",temp2->coeff,temp2->expo);
            temp2=temp2->next;
        }
    }
    else
    {
        while(temp1!=NULL)
        {
            printf("%dx^%d",temp1->coeff,temp1->expo);
            temp1=temp1->next;
        }
    }
}
void main()
{
    struct node *head1=NULL,*head2=NULL,*head3=NULL;
    struct node *a,*b,*k;
    int choice=0;
    while(choice<6)
    {
        printf("\nOperations on Single linked list are:\n");
        printf("1.Creation of 1st polynomial\n");
        printf("2.Creation of 2nd polynomial\n");
        printf("3.Display of 1st polynomial\n");
        printf("4.Display of 2nd polynomial\n");
        printf("5.Add polynomials\n");
        printf("Others:Exit()\n");
        printf("Enter your choice:\n");
        scanf("%d",&choice);
        switch(choice)
        {
            case 1:
                    printf("\nEnter 1st polynomial:\n");
                    a=create(head1);
                    break;
            case 2:
                    printf("\nEnter 2nd polynomial:\n");
                    b=create(head2);
                    break;
            case 3:
                    printf("\nThe 1st polynomial is:\n");
                    display(a);
                    break;
            case 4:
                    printf("\nThe 2nd polynomial is\n");
                    display(b);
                    break;
            case 5:
                    add_polynomial(a,b);
                    break;
        }
    }
    
}
