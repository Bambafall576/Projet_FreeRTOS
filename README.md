# Projet_FreeRTOS

Ce projet consiste à faire un programme sur Arduino en utilisant FreeRTOS pour accomplir les tâches suivantes :
•	Tache1 : 
Récupère une valeur analogique sur l’entrée A0 qui est branchée avec un potentiomètre puis l’envoie à la tâche 3 (valeur entre 0 et 1023) 
•	Tache2 : 
Récupère une valeur numérique qui est la résultante de l'addition des deux valeurs des deux entrées numérique 3 et 4 qui sont branchées avec des boutons
poussoirs en montage pull down, puis envoie cette valeur numérique à la tâche 3 (valeur entre 0 et 2) 
•	Tache3 :
Reçoit les deux valeurs des tâches 1 et 2 puis les mets dans une structure en ajoutant la valeur de la fonction millis() 
struct valeurCapteurs {
    int analogique;
    int numérique;
    double tempsEnMillisecondes;
};
Une fois la structure remplie, cette dernière doit être envoyée à la tâche 4.
•	Tache4 : 
Cette tâche reçoit la valeur de la structure et utilise le port série pour l’afficher, ensuite envoie cette structure à la tâche 5.
•	Tache5 : 
Cette tâche doit transformer la valeur du temps dans la structure en minutes, ensuite elle doit afficher cette nouvelle structure à travers le port série.

Pour ce faire, on a dû utiliser dans notre code : les sémaphore (mutex) pour protéger l’utilisation du port série entre les taches 4 et 5
pour l’affichage des données et les Queue pour prendre en compte les files d’attentes et ainsi communiquer les informations 
