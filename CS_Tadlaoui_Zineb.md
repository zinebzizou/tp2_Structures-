# **Algorithmique et programmation avancée**
<br>


##  Objectif : Manipulation des structures
<br>



Un semestre est composé de 6 modules, chaque module est enseigné par un professeur et suivis par des
étudiants. Chaque module à 3 notes: TP + Contrôle + Examen. La direction à décider de stocker les notes par un tableau de structures et de les gérer par un programme C. on suppose qu'un étudiant et enseignant sont caractérisés par un Code, un Nom, filière.
Un module est caractérisé par un code, un nom, un enseignant, les étudiants, les notes.


<br>
<br>


> **Définir les structures étudiant, enseignant, notes et modules**
> <br>

```java script
//la structure etudiant (un etudiant se caracterise par un nom, un code et une filiere)
struct etudiant{
int code;
char nom[20];
char filiere[20];
} ETUDIANT;

//la structure enseignant (un enseignant se caracterise par un nom, un code et une filiere)
typedef struct ENSEIGNANT{
int code;
char nom[20];
char filiere[20];
}enseignant;

//la structure note (la note se compose de trois notes: une note de tp, une de comtrole et une d examen)
typedef struct notes{
int tp;
int controle;
int examen;
} NOTES;

//la structure module  assemble toutes les structures precedentes
typedef struct modules{
int code;
char nom[20];
ETUDIANT eleve;
ENSEIGNANT professeur;
NOTES note;
}MODULEs;
```
<br>

> **Ecrire une fonction qui saisit un étudiant**
> <br>

```java script
//fonction qui nous permet de saisir les informations d'un etudiant
void SaisirEtudiant(ETUDIANT *c){
    //on demande a l utilisateur de saisir le code
    printf("Veuillez entrer le code : ");
    //puis on stock la valeur entree par l utilisateur dans 'code'
    scanf("%d",&c->code);
    //on demande a l utilisateur de saisir le nom
    printf("Veuillez entrer le nom de l etudiant: ");
    //puis on stock la valeur entree par l utilisateur dans 'nom'
    scanf("%s",&c->nom);
    //on demande a l utilisateur de saisir la filiere
    printf("Veuillez entrer la filiere : ");
   //puis on stock la valeur entree par l utilisateur dans 'filiere'
    scanf("%s",&c->filiere);
}
```
<br>

>  **Ecrire une fonction qui affiche un étudiant**
> <br>

```java script
//fonction pour afficher l etudiant saisi dans la fonction precedente
void AfficheerEtudiant(ETUDIANT *c){
    printf("\n le code est: %d \n le nom est : %s\n et la filiere est : %s\n",c->code,c->nom,c->filiere);
}
```
<br>

>  **Ecrire une fonction qui saisit un enseignant**
> <br>

```java script
//fonction qui nous permet de saisir les informations d'un enseignant
void SaisirEnseignant(ENSEIGNANT *e){
    //on demande a l utilisateur de saisir le code
    printf("Veuillez entrer le code : ");
     //puis on stock la valeur entree par l utilisateur dans 'code'
    scanf("%d",&e->code);
     //on demande a l utilisateur de saisir le nom
    printf("Veuillez entrer le nom : ");
    //puis on stock la valeur entree par l utilisateur dans 'nom'
    scanf("%s",&e->nom);
    //on demande a l utilisateur de saisir la filiere
    printf("Veuillez entrer la filiere: ");
    //puis on stock la valeur entree par l utilisateur dans 'filiere'
    scanf("%s",&e->filiere);
}
```
<br>

>  **Ecrire une fonction qui affiche un enseignant**
> <br>

```java script
// fonction pour afficher un enseignant saisi
void AfficherEnseignant(ENSEIGNANT *e){
    printf("\n le code de l'ensignant est: %d \n le nom est : %s\n et la filiere est : %s\n",c->code,c->nom,c->filiere);
}
```
<br>

> **Ecrire une fonction qui saisit les notes**
> <br>

```java script
void SaisirNotes(NOTES *N){
    //on demande a l utilisateur d'entrer la note du tp
    printf(" Veuillez entrer la note du TP: ");
    //puis on stock la valeur entree par l utilisateur dans 'tp'
    scanf("%d",&N->tp);
    //on demande a l utilisateur d'entrer la note du controle
    printf(" Veuillez entrer la note du controle: ");
    //puis on stock la valeur entree par l utilisateur dans 'controle'
    scanf("%d",&N->controle);
    //on demande a l utilisateur d'entrer la note de l'examen
    printf("Veuillez entrer la note d'examen: ");
    //puis on stock la valeur entree par l utilisateur dans 'examen'
    scanf("%d",&N->examen);
}
```
<br>

> **Ecrire une fonction qui affiche les notes**
> <br>

```java script
//fonction pour afficher la note saisi
void AfficheeNotes(NOTES *N){
    int moy;
    //calculons la moyenne des notes
    moy=(N->tp+N->controle+N->examen)/3;
    printf("\n la note du TP est :%d\n la note du controle est :%d\n la note d'exam est :%d\n la moyenne : %d\n",c->tp,c->control,c->exam,moy);
}
```
<br>

> **Ecrire une fonction qui saisit un module**
> <br>

```java script
//fonction qui nous permet de remplir un module
void SaisirModule(MODULE *M){
    //on demande a l utilisateur d'entrer le code 
    printf(" Veuillez entrer le code: ");
    //puis on stock la valeur entree par l utilisateur dans 'code'
    scanf("%d",&M->code);
    //on demande a l utilisateur d'entrer le nom 
    printf(" Veuillez entrer le nom: ");
    scanf("%s",&M->nom);
     //pour avoir les infos de l'enseignant on fait appel a la fonction SaisirETUDIANT et puis on stock les infos sur 'eleve'
    saisiretudiant(&M->eleve);
    //pour avoir les infos de l'enseignant on fait appel a la fonction SaisirEnseignant et puis on stock les infos sur 'professeur'
    SaisirENSEIGNANT(&M->professeur);
    //pour avoir les notes on fait appel a la fonction SaisireNotes et puis on stock les infos sur 'note'
    SaisirNotes(&M->note);
}
```
<br>

> **Ecrire une fonction qui affiche un module**
> <br>

```java script
//pour afficher un module complet
void AfficherModule(MODULE *M){

    printf("\nle code du module est:%d\n et le nom est ;%s\n",c->code,c->nom);
    //pour afficher un enseignant
    AfficherENSEIGNANT(&M->professeur);
     //pour afficher un etudiant
    AfficheEtudiant(&M->eleve);
     //pour afficher les notes 
    AfficherNotes(&M->note);
}
```
<br>

> **Ecrire une fonction qui saisit un tableau de modules**
> <br>

```java script
//pour remplir un tableau de modules
void TableauModule(MODULE *c,int taille){
    int i;
    //la boucle va demander jusqu'a la taille de tableau de remplir un module
    for (i=0; i<taille;i++)
    {
        //on  fait appel a la fonction SaisirModule pour saisir les infos du module 
        SaisirModule(&c[i]);
    }    
}
```
<br>

> **Ecrire une fonction qui affiche un tableau de modules**
> <br>

```java script
//pour afficher le tableau de module remplis dans la fonction precedente
void AffichertabModule(MODULE *c,int taille){
    int i;
    for ( i=0; i<taille;i++)
    {
        //on fait  appel a la fonction AfficherModule
        AfficherModule(&c[i]);
        
    }  
}
```
<br>

> **Ecrire le programme principal qui réalise le scénario suivant :**

*  Déclaration d'un tableau dynamique de modules.
*  Saisie d'un tableau de modules.
*  Affichage d'un tableau de modules.
> <br>

```java script
// dans le programme principale 
int main(){
 //on declare une taille avec laquelle on va travailler
int taille=1;
//on declare un etudiant
ETUDIANTS E;
//on declare un enseignant 
ENSEIGNANT  C;
//on declare une note
NOTES N;
//on declare un module
MODULES M;
//on declare une taille avec laquelle on va travailler
int taille=1;
TableauModule(&M, taille);
AffichertabModule(&M,taille);

}

```
<br>

> **Ecrire une fonction qui calcule le nombre des étudiants qui suivent un module donné**
> <br>

```java script
//pour calculer les etudiants qui suivent un module donne
int  SuivisModule(MODULE *c,int taille,char mod[30]){
    int i,counter=0;
    for(i=0;i<taille;i++){
        if(strcmp(c[i].nom,mod)==0){
            counter++;
        }
    }
    return counter;
}
```
<br>

> **Ecrire une fonction qui affiche les modules suivis par un étudiant donné**
> <br>

```java script
//fonction nous permet d'afficher les modules suivis par te etudiant
void AfficherModuleSuivis(MODULE *c,int taille,char eleve[10]){
    int i;
    for(i=0;i<taille;i++){
        if(strcmp(c[i].eleve.nom,eleve)==0){
             AfficherModule(&c[i]);
    }    
        }
}}
```
<br>

> **Ecrire une fonction qui calcule la moyenne du module d'un étudiant donnée**
> <br>

```java script
//pour calculer la moyenne des modules de l'etudiant
void MoyenneModule(MODULE *c,int taille,char eleve[20]){
    int i,j=0;
    for(i=0;i<taille;i++){
        if(strcmp(c[i].eleve.nom,eleve)==0){
            int moyenne=(c[i].note.tp+c[i].note.controle+c[i].note.examen)/3;
            printf("\nla moyenne  est %d",moyenne);

}}
}
```
<br>

> **Ecrire une fonction qui calcule la moyenne du semestre d'un étudiant donné**
> <br>

```java script
void MoyenneSemestre(MODULE *c,int taille,char etu[20]){
    int i,j=0;
    for(i=0;i<taille;i++){
        if(strcmp(c[i].eleve.nom,eleve)==0){
            int moy=(c[i].note.tp+c[i].note.control+c[i].note.exam)/3;
            j+=moy;
int finalmoy=j/(taille-1);
}} printf("\nla moyenne du semestre est :%d",finalmoy);
}
```
<br>

---


<br>


## **Réalisé par : Tadlaoui Zineb (CS)**
## **Encadré par : Pr.AMAMOU Ahmed**

<br>

---

# **Merci**
