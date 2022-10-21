Au préalable :
```
cp /usr/share/man/man1/man.1.gz .
gunzip man.1.gz
grep -E "mon_expression" man.1
```

1. Motif en début

- Chercher toutes les lignes commençant par **a** 

*grep -E "^a" man.1*

- Chercher toutes les lignes commençant par **A**

*grep -E "^A" man.1*

- Chercher toutes les lignes commençant par **a** ou **A**

*grep -E "^[aA]" man.1*

2. Chercher toutes les lignes finissant par **of**

*grep -E "of$" man.1*

3. Chercher toutes les lignes contenant au moins un chiffre.

*grep -E "[0-9]" man.1 ou grep -E [[:digit:]] man.1*

4) Chercher toutes les lignes commençant par une majuscule.

*grep -E "^[A-Z]" man.1*

5) Chercher toutes les lignes commençant par «B», «E» ou «Q».

*grep -E "^[BEQ]" man.1 ou grep -E "^(B|E|Q)" man.1*

6) Chercher toutes les lignes ne finissant pas par un point ou une virgule

*grep -E "[^.,]$" man.1*

7) Chercher tous les mots contenant un «r» précédé de n'importe quelle lettre majuscule ou minuscule.

*grep -Eo "[A-Za-z]+r[A-Za-z]*" man.1 #ajout de l'option -o pour ne sortir que les matchs ou grep -Eo "[[:alpha:]]+r[[:alpha:]]*" man.1*

8) Chercher tous les mots dont la seconde lettre est un «r».

*grep -Eow "[A-Za-z]r[A-Za-z]*" man.1 ou  grep -Eow "[[:alpha:]]r[[:alpha:]]*" man.1* l'option w va selectionner uniquement les mots correspondants à l'expression
