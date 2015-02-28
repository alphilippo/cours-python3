# Branchements conditionnels

> -- Quarante-deux ! cria Loonquawl. Et c'est tout ce que t'as à nous montrer au
> bout de sept millions et demi d'années de boulot ?
>
> -- J'ai vérifié très soigneusement, dit l'ordinateur, et c'est
> incontestablement la réponse exacte. Je crois que le problème, pour être tout
> à fait franc avec vous, est que vous n'avez jamais vraiment bien saisi la
> question.

> *Douglas Adams -- Le Guide du Voyageur Galactique*

Vous ne vous en doutez sûrement pas, mais dans la totalité des programmes qu'il
exécute, l'ordinateur passe son temps à **se poser des questions**. Oh, bien
sûr, il ne se demande pas ce qu'il va manger ce soir ni quel est le sens de sa
vie, mais il se pose des questions d'ordinateur, qui lui permettent de décider
*ce qu'il va faire ensuite*.

Par exemple, imaginons un programme qui demande à son utilisateur d'entrer son
mot de passe pour exécuter une action. À un moment donné de ce programme,
l'ordinateur va devoir décider si le mot de passe entré par l'utilisateur est
le bon, et il exécutera une action différente suivant que ce soit le cas ou
non. Ce genre de carrefour dans l'exécution d'un programme s'appelle un
**branchement conditionnel**, et c'est ce que nous allons étudier tout au long
de ce chapitre.

Dans ce chapitre, nous allons apprendre :

* ce qu'est une valeur **booléenne**,
* la notion de **prédicat**,
* à effectuer différentes actions dans différentes conditions.

## Notre programme d'exemple

Voici un programme qui illustre ce que nous allons apprendre dans ce chapitre :

```python
MOT_DE_PASSE = 'abracadabra'

saisie = input("Saisissez votre mot de passe : ")

if saisie == MOT_DE_PASSE:
    print("Accès autorisé")
else:
    print("Accès refusé")
```

Nous allons découvrir dans la suite comment celui-ci fonctionne en détail.
Contentons nous de jouer avec dans un premier temps.

### Écrire un programme dans un fichier

À partir de ce chapitre, nous allons travailler sur des programmes d'exemple.
Il existe bien des façons d'exécuter un programme en Python suivant votre
système d'exploitation. Pour ne pas surcharger le propos, je me contenterai de
vous montrer ici la méthode qui marchera chez tout le monde.

Ouvrez le programme IDLE livré avec Python. Vous devriez voir apparaître une
fenêtre dans le style de la figure 1.

![La console IDLE](src/img/idle.png)

Puis cliquez sur `File -> New File` ou bien appuyez simultanément sur les
touches `<Ctrl>` et `<N>`.


Ceci devrait faire apparaître une fenêtre vide dans laquelle vous pouvez écrire
un programme en Python. Recopiez dedans notre programme d'exemple, comme sur
la figure 2.

![Notre programme d'exemple](src/img/programme_motdepasse.png)

Enfin, exécutez ce programme en appuyant sur la touche `<F5>`. IDLE va vous
demander si vous souhaîtez sauvegarder ce fichier au passage, enregistrez-le en
lui donnant l'extension `.py`, par exemple sous le nom `motdepasse.py`. Une
fois ceci fait, le programme se lance dans la console interactive, comme sur la
figure 3.

![Exécution](src/img/execution.png)

Essayez d'exécuter plusieurs fois ce programme avec des mots de passe
différents, puis essayez avec le bon : abracadabra. Comme vous pouvez le
constater, le programme n'affiche "Accès autorisé" que si vous lui entrez le
bon mot de passe.

### Jouons !

Avant même de chercher à comprendre comment ce script marche, essayez de le
modifier pour changer son comportement. Par exemple:

* Faites en sorte que le mot de passe soit autre chose que « abracadabra ».

* Traitez l'utilisateur d'idiot lorsqu'il entre le mauvais mot de passe.

C'est une bonne habitude à prendre lorsque vous êtes confronté à un code de ce
cours : réussir à bidouiller un programme pour lui faire faire ce que l'on
veut, c'est beaucoup plus efficace qu'un long discours théorique !

## Vrai ou faux ?

### Les booléens

Je vous ai dit plus haut que même si l'ordinateur se pose des questions à
longueur de temps, il ne peut pas se poser n'importe lesquelles. En fait, les
questions qu'il se pose sont des questions *logiques*, c'est-à-dire qu'elles
n'acceptent que deux réponses possibles : oui ou non.

Par exemple, nous pouvons demander à Python si 2 est inférieur à 38.

Pour cela, nous allons formuler notre question d'une façon qui va peut-être
sembler bizarre. En fait, nous allons *affirmer* que 2 est inférieur à 38, et
Python nous répondra que c'est vrai, au moyen de la valeur spéciale `True` :

```python
>>> 2 < 38
True
```

À l'inverse, si on lui dit que 7 est inférieur à 4, Python nous répondra que
c'est faux :

```python
>>> 7 < 4
False
```

En programmation, une expression qui peut être vraie (`True`) ou fausse
(`False`) s'appelle **un prédicat**, et les deux valeurs de vérité possibles
d'un prédicat sont un type d'objet à part entière, c'est le type **booléen**.
En Python, c'est le type `bool` :

```python
>>> type(True)
<class 'bool'>
>>> type(False)
<class 'bool'>
```

### Opérateurs de comparaison
