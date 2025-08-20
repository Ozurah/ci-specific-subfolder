# ci-specific-subfolder
Tester l'exécution de la CI que pour certains dossiers

Exemple une étape ne doit être exécutée que si les changements ont eu lieu au minimum dans le dossier A
Ou l'étape ne doit pas se déclancher si les changements n'ont lieu que dans le dossier C

# Observations

Pour les step :
    La détection des dossiers se font via les différences sur la branche principale
    Donc dans le cas d'un edit sur une branche, chaque dossier différents de la branche principale va lancer son étape
    
Pour le workflow (condition générale):
    Ne semble pas se relancer si le dossier n'est pas modifié au moment au push
    Si le dossier a été modifié depuis le dernier push, il se lance correctement
