# Présentation

Vous commencez à écrire vos premiers programmes et ces derniers deviennent de
plus en plus complexes. Vous rendre compte que vous voulez parfois effectuer
plusieurs fois la même opération en différents endroits de votre code. Vous
avez alors probablement été tenté de faire un copier-coller de ces parties
redondantes. Et là, malheur : vous vous rendez compte après plusieurs
copier-coller que ce bout de code contient un bug. Il va alors falloir
retrouver et corriger chaque utilisation de ce code dans tout votre code pour
le rendre fonctionnel. Un vrai cauchemar en perspective.

## La solution : les fonctions

Les fonctions sont des bouts de code d'un programme qui sont exécutés à chaque
fois qu'ils sont appelés. Ainsi, par exemple, vous avez plusieurs fois besoin
d'afficher une liste de choix dans votre console. Vous allez alors écrire ce
code une première fois et le marquer comme fonction : on dit que l'on *définit*
une fonction. Vous pourrez alors, à chaque fois que cela est nécessaire,
*appeler* cette fonction. Ceci aura pour effet de déclencher le code présent
dans ladite fonction et, dans notre cas, d'afficher notre superbe menu.

Que se passe-t-il si nous définissons plusieurs fonctions ? Comment les
différencier? Et bien, on appelle une fonction par son *nom*. Ce dernier est
défini au moment de la création de la fonction. C'est pourquoi, il est
conseiller de donner des noms clairs et explicits à vos fonctions. Ceci vous
permettra de ne pas chercher le nom de votre fonction et de vous souvenir de
son utilité plus facilement. Par exemple, `affiche_menu` est un nom clair
décrivant le rôle de cette fonction et facile à retenir comparer à un nom plus
court donné à la va-vite tel que `f1`.

Revenons sur les avantages de cette méthode : votre code est maintenant plus
court car l'affichage de votre menu est définit à un endroit unique au lieu de
se répéter plusieurs fois. De plus, si vous voulez modifier les choix de votre
menu ou corriger un bug, il vous suffit maintenant de modifier la
*déclaration*, aussi appeler *définition*, de la fonction. Ce changement se
répercutera alors automatiquement sur tous vos appels à cette fonction.

> Il faut également noter que rien n'empêche une fonction d'en appeler une
> autre. Par exemple `affiche_menu` pourrait d'abord appeler une fonction
> 'efface_console'.
>
> Une fonction peut même s'appeler elle-même : c'est la *récursivité*.

# Les fonctions en Python

Abordons maintenant l'implémentation en Python de ce concept de fonction. Nous
allons continuer sur notre exemple précédent et créer une fonction
`affiche_menu`. La *définition* d'une fonction suis la structure suivante :

```python
#Code hors fonction
def nom_fonction():
    #Code de la fonction
#Code hors fonction
```

Détaillons un peu tout ça. `def` est le mot clé indiquant à Python que l'on est
en train de définir une fonction. `nomFonction` est le nom de la fonction.
C'est celui que nous utiliserons pour appeler la fonction. Viens ensuite le
code de la fonction qui sera exécuté à chaque appel. Noter bien l'indentation
du code dans la fonction. La réduction d'un niveau d'indention délimite la fin
de la fonction.

Voyons maintenant ce que pourrais donner notre fonction exemple :

```python
def affiche_menu():
    print("Menu :")
    print("* Action 1")
    print("* Action 2")
    #Et ainsi de suite
```
Maintenant, à chaque fois que vous voulez afficher ce menu, il suffit
d'utiliser :

```python
#Du code
affiche_menu()
#Encore du code
```

Il est néanmoins très probable qu'après l'appel de cette fonction, vous
utilisiez `input` pour récupérer le choix de l'utilisateur. Cette instruction
est redondante est devrait donc faire partie de la fonction. Cependant, le
traitement de la réponse ne devrait pas se trouver dans la fonction car il se
peut qu'il ne soit pas partout le même. Il serait alors pratique de pouvoir
renvoyer un résultat, un peu à la manière de `input` justement.

## Renvoyer un résultat

*Renvoyer* ou *retourner* un résultat s'effectue à l'aide du mot-clé `return`
suivit de ce que vous désirez renvoyer. Quelque exemples :

```python
return True #renverra toujours la même valeur.
return var #où var est une variable définit précédemment. La valeur renvoyer peut alors être différentes selon les cas
return input("Sélection: ") #on peut également renvoyer le retour d'une autre fonction.
```

Notre exemple devient alors :

```python
def affiche_menu():
    print("Menu :")
    print("* Action 1")
    print("* Action 2")

    return input("Choix: ") #renvoie le choix de l'utilisateur
```

> Il faut noter que `return` interrompt la fonction, c'est à dire que tout code
> se trouvant après un `return` ne sera pas exécuté.
>
> ```python
> return False
> print("Non") #ne sera pas exécuté
> ```
> Cependant :
>
> ```python
> if 'toto' == input():
>     return False
> print("Non") #sera exécuté si le texte tapé est différent de 'toto'
> ```

On obtient alors :

```python
choix = affiche_menu()
```

## Les paramètres

Vous commencez maintenant à avoir plusieurs fonctions mais certaines d'entre
elles ont des comportements très semblables. Par exemple, supposons que nous
avons une fonction `dire_bonjour` et une autre `dire_au_revoir`. Vous voulez
maintenant créer une fonction `dire_une_blague`. Toutes ces fonctions se
ressemble au niveau de leur code et ne diffèrent que peu. Il semble alors que
nous soyons à nouveau en train d'effectuer des copier-coller.

C'est alors qu'entrent en scène les paramètres. Ceux-ci permettent de *passer en
argument* des informations variables à votre fonction pour que celle-ci puisse
modifier son comportement. Voici un exemple pour y voir plus clair :

```python
def dire(texte):
    print('# '+texte)

dire('Bonjour') #affiche `# Bonjour`
dire('Au revoir') #affiche `# Au revoir`
```

Ainsi, nous pouvons nous débarrasser des fonctions `dire_bonjour` et
`dire_au_revoir` et n'avoir plus qu'une seule fonction. On dit que `texte` est
un paramètre. Une fois dans le corps de votre fonction `texte` peut être utilisé
comme une variable ordinaire : vous pouvez lui appliquer des conditions, la
modifier, la passer en paramètre à une autre fonction, ...

Vous pouvez avoir plusieurs paramètres pour une seule fonction. IL vous suffit
de les séparer par des virgules dans la déclaration de votre variable :

```python
def addition(a,b):
    return a+b

addition(10,5) #renvoie 15
addition(10)
```

Le dernier appel renvoie l'erreur suivante :

```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: addition() missing 1 required positional argument: 'b'
```

En effet, vous *devez* passer à votre fonction le nombre de paramètre attendu
par celle-ci. C'est pourquoi le deuxième appel a retourné une erreur : nous
n'avons passé qu'un seul paramètre au lieu de deux. Dans le cas de notre
fonction, cela semble logique car pour faire une addition, nous avons besoin de
deux valeurs. Cependant, ce comportement peut être parfois génant. Imaginons la
fonction `saluer` qui prend en paramètre le nom de la personne à saluer. Il
serait pratique de pouvoir l'appeler sans paramètre dans le cas où nous ne
connaissons pas le nom de l'utilisateur. Nous allons voir comment réaliser une
telle fonction.

## Paramètres optionnels

Reprenons notre fonction :

```python
def saluer(nom):
    print('Bonjour '+nom)
```
Nous allons maintenant rendre le paramètre `nom` *optionnel*. Pour ce faire, on
utilise la syntaxe `param = valeur` dans la définition de la fonction, où
`valeur` est la *valeur par défaut* du paramètre. Un exemple :

```python
def saluer(nom = 'Visiteur'):
    print('Bonjour '+nom)

saluer('Clem') #affiche `Bonjour Clem`
saluer() #affiche `Bonjour Visiteur`
```

Vous pouvez ajoutez plusieurs paramètres optionnels et même combiner paramètres
optionnels et obligatoires. La seule condition est que tout vos paramètres
obligatoires doivent se trouver au début, et tout ceux facultatifs à la fin de
la signature, par exemple `def fonction(a, b, c = 1)` et non `def fonction(a, c
= 1, b)`.

# La portée des variables

## Les variables globales

# Les fonctions anonymes

# TP : Calcul Fractionnaire
