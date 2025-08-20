# ci-specific-subfolder
Tester l'exécution de la CI que pour certains dossiers

Exemple une étape ne doit être exécutée que si les changements ont eu lieu au minimum dans le dossier A
Ou l'étape ne doit pas se déclancher si les changements n'ont lieu que dans le dossier C

# Observations

Pour les step :
- La détection des dossiers se font via les différences sur la branche principale
    Donc dans le cas d'un edit sur une branche, chaque dossier différents de la branche principale va lancer son étape
    
Pour le workflow (condition générale):
- Ne semble pas se relancer si le dossier n'est pas modifié au moment au push
- Si le dossier a été modifié depuis le dernier push, il se lance correctement

- En cas de plusieurs chemins dans "paths-ignore", ça agit comme des "OU"
    ```
    paths-ignore:
    - 'A/**'
    - 'B/**'
    ```
    ==> Il faut une modification dans un moins 1 fichier en dehors du dossier A ou du dossier B pour qu'il soit déclanché

# Liens

Conditions au workflow
    https://docs.github.com/fr/actions/reference/workflows-and-actions/workflow-syntax#onpushpull_requestpull_request_targetpathspaths-ignore
    
Condition aux étapes
    https://github.com/dorny/paths-filter#examples