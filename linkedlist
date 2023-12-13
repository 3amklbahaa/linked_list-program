#include <stdio.h>
#include <stdlib.h>
typedef struct node{
    int id;
    struct node* next;
}node;
struct node* create_node(){
    struct node* node;
    node = (struct node*)malloc(sizeof(struct node));
    return node;
}
int SearchVersion1(struct node* head,int id ) {
    if (head == NULL) {
        return -1;
    }
    struct node *current = head;
    while (current->next != NULL) {
        if (current->id == id) {
            return current->id;
        }
        current = current->next;
    }
    return -1;
}
struct node* SearchVersion2(struct node* head,int id){
    if(head==NULL){
        return NULL;
    }
    struct node* current = head;
    while(current->next!=NULL){
        if(current->id == id){
            return current;
        }
        current = current->next;
    }
    return NULL;
}
int size(struct node* head){
    if(head==NULL){
        return 0;
    }
    int count = 0;
    struct node* current = head;
    while(current!=NULL){
        count ++;
        current=current->next;
    }
    return count;
}
void InsertHead(struct node **head, int id){
    struct node *temp = (struct node *)malloc(sizeof(struct node));
    if(temp==NULL){
        return;
    }
    temp->id=id;
    temp->next= *head;
    *head = temp;
}
void InsertTail(struct node **head, int id){
    struct node *temp = (struct node *)malloc(sizeof(struct node));
    if(temp==NULL){
        return;
    }
    struct node* current = *head;
    while(current->next!=NULL){
        current=current->next;
    }
    temp->id=id;
    current->next=temp;
}
int RemoveHead(struct node **head){
    if(*head==NULL){
        return -1;
    }
    struct node* temp = *head;
    *head = (*head)->next;
    int ReturnId = temp->id;
    free(temp);
    return ReturnId;
}
int RemoveTail(struct node** head){
    if(*head==NULL){
        return -1;
    }
    struct node* temp = *head;
    struct node* prev = NULL;
    while(temp->next!=NULL){
        prev = temp;
        temp = temp->next;
    }
    if (prev==NULL) {
        *head=NULL;
    }
    else{
        prev->next = NULL;
    }
    int id = temp->id;
    free(temp);
    return id;
}
int insert(struct node** head, int id, int pos){
    if(pos<0){
        return -1;
    }
    struct node* new = (struct node*)malloc(sizeof(struct node));
    if(new==NULL){
        return -1;
    }
    new->id=id;
    new->next = NULL;
    if(pos==0){
        new->next = *head;
        *head = new;
        return 0;
    }
    struct node* temp = *head;
    for(int i=0;i<pos-1&&temp!=NULL;i++){
        temp = temp->next;
    }
    if(temp==NULL){
        free(new);
        return -1;
    }
    new->next = temp->next;
    temp->next=new;
    return  0;
}
int Remove(struct node** head, int pos){
    if(pos<0){
        return -1;
    }
    struct node * temp = *head;
    if(pos==0){
        if(temp==NULL){
            return -1;
        }
        *head = temp->next;
        free(temp);
        return 0;
    }
    struct node *prev = NULL;
    for(int i=0;i<pos&&temp!=NULL;i++){
        prev=temp;
        temp = temp->next;
    }
    if(temp==NULL){
        return -1;
    }
    prev->next = temp->next;
    free(temp);
    return 0;
}
int main() {
    struct node *head = NULL;
    while (1) {
        printf("\nMenu:\n");
        printf("1. Calculer et afficher la taille de la liste\n");
        printf("2. Rechercher un élément dans la liste\n");
        printf("3. Insérer un élément en tête de liste\n");
        printf("4. Insérer un élément à la fin de la liste\n");
        printf("5. Insérer un élément à une position donnée de la liste\n");
        printf("6. Supprime la tête de liste\n");
        printf("7. Supprime la queue d'une liste\n");
        printf("8. Supprime le nœud à une position donnée dans la liste\n");
        printf("9. Quittez le programme\n");
        int choice;
        printf("Choisissez une option : ");
        scanf("%d", &choice);
        int id, pos, result;
        switch (choice) {
            case 1:
                printf("La taille de la liste est : %d\n", size(head));
                break;
            case 2:
                printf("Entrez l'ID à rechercher : ");
                scanf("%d", &id);
                result = SearchVersion1(head, id);
                if (result != -1) {
                    printf("L'ID %d a été trouvé dans la liste.\n", result);
                } else {
                    printf("L'ID %d n'a pas été trouvé dans la liste.\n", id);
                }
                break;
            case 3:
                printf("Entrez l'ID à insérer en tête de liste : ");
                scanf("%d", &id);
                InsertHead(&head, id);
                break;
            case 4:
                printf("Entrez l'ID à insérer à la fin de la liste : ");
                scanf("%d", &id);
                InsertTail(&head, id);
                break;
            case 5:
                printf("Entrez l'ID à insérer : ");
                scanf("%d", &id);
                printf("Entrez la position : ");
                scanf("%d", &pos);
                result = insert(&head, id, pos);
                if (result == 0) {
                    printf("L'élément a été inséré avec succès à la position %d.\n", pos);
                } else {
                    printf("Erreur lors de l'insertion à la position %d.\n", pos);
                }
                break;
            case 6:
                result = RemoveHead(&head);
                if (result != -1) {
                    printf("La tête de la liste a été supprimée. ID supprimé : %d\n", result);
                } else {
                    printf("La liste est vide. Aucun élément à supprimer.\n");
                }
                break;
            case 7:
                result = RemoveTail(&head);
                if (result != -1) {
                    printf("La queue de la liste a été supprimée. ID supprimé : %d\n", result);
                } else {
                    printf("La liste est vide. Aucun élément à supprimer.\n");
                }
                break;
            case 8:
                printf("Entrez la position du noeud à supprimer : ");
                scanf("%d", &pos);
                result = Remove(&head, pos);
                if (result == 0) {
                    printf("Le nœud à la position %d a été supprimé avec succès.\n", pos);
                } else {
                    printf("Erreur lors de la suppression du nœud à la position %d.\n", pos);
                }
                break;
            case 9:
                while (head != NULL) {
                    RemoveHead(&head);
                }
                printf("Programme quitté avec succès.\n");
                return 0;
            default:
                printf("Option invalide. Veuillez choisir une option valide.\n");
        }
    }
    return 0;
}
