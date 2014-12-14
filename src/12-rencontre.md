# Rencontre du troisième type

> Le renard se tut et regarda longtemps le petit prince :
>
> -- S'il te plaît... apprivoise-moi ! dit-il.
>
> -- Je veux bien, répondit le petit prince, mais je n'ai pas beaucoup de
> temps. J'ai des amis à découvrir et beaucoup de choses à connaître.
>
> -- On ne connaît que les choses que l'on apprivoise, dit le renard.

> *Antoine de Saint-Exupéry -- Le Petit Prince*


Maintenant qu'un Python habite dans votre ordinateur, il est temps de faire sa
connaissance. Dans ce chapitre, nous allons visiter son habitat naturel : la
console interactive, que vous utiliserez tout le temps pour tester vos
programmes. Ce sera votre lieu de rencontre privilégié, puisque c'est ici que
vous pourrez *dialoguer* avec lui.

Suivez moi ! Il nous attend déjà.

## Contact

Nous voici devant l'antre de la bête.

Commençons par l'appeler, si vous le voulez bien. Pour cela, lancez
l'interpréteur de commandes Python comme je vous l'ai montré dans le chapitre
précédent (en tapant "`python3`" ou bien "`py -3`" dans votre console, suivant
votre système d'exploitation).

Sa queue se déroule dans la console, et le voilà qui vous fixe de ses grands
yeux verts :

```python
Python 3.4.0 (default, Apr 11 2014, 13:05:11)
[GCC 4.8.2] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

Ces trois chevrons (`>>>`) constituent **l'invite de commande**. C'est la façon
dont Python vous signale qu'il vous écoute et qu'il attend vos instructions.
Montrez-vous bien élevé, saluez-le et validez en appuyant sur la touche
`<Entrée>`.

```python
>>> Bonjour
Traceback:
  File "<stdin>", line 1, in <module>
NameError: name 'Bonjour' is not defined
```

Ouh là, attention, reculez ! Vous l'avez contrarié.

Ce que Python vient de vous cracher au visage, c'est un message qui signifie
qu'il n'a pas compris ce que vous lui dites. En effet, pour créer un programme,
il ne suffit pas de donner des ordres en français à votre interpréteur. Il faut
que vous lui parliez **en Python**, et c'est justement ce que vous êtes venu
apprendre.

Pour le moment je vais vous aider. Entourez donc votre phrase avec des
guillemets (`"`), comme ceci :

```python
>>> "Bonjour"
'Bonjour'
```

Le voilà plus coopératif. Python vous a renvoyé la politesse. Poursuivons :

```python
>>> "Je m'appelle Arnaud. Et toi ?"
"Je m'appelle Arnaud. Et toi ?"
>>> "Mais, je te l'ai déjà dit..."
"Mais, je te l'ai déjà dit..."
>>> "Hé ! Tu arrêtes de répéter tout ce que je dis ?!"
'Hé ! Tu arrêtes de répéter tout ce que je dis ?!'
```

Rassurez-vous : aussi taquin soit-il, Python n'est pas vraiment en train de se
moquer de vous. Laissez-moi vous expliquer.

Le rôle de cette console interactive est d'**interpréter** les instructions que
vous lui soumettez. Chaque fois que vous appuyez sur `<Entrée>`, vous envoyez
l'expression que vous venez de taper à Python, celui-ci l'évalue et vous
retourne *sa valeur*. Jusqu'ici, vous lui avez envoyé des expressions qui ont
toutes la même forme : du texte entouré de guillemets. Il s'agit de données de
base que peut manipuler l'interpréteur et que l'on appelle des *chaînes de
caractères*. Python s'est contenté d'évaluer ces données, et de vous retourner
leurs valeurs telles qu'il les a comprises, c'est-à-dire qu'il vous a renvoyé
les chaînes telles quelles.

Nous reparlerons très bientôt des chaînes de caractères. Pour l'heure, si nous
essayions de lui faire évaluer des choses plus utiles ?

## Une bête de calcul

Je vous ai dit que la console interactive sert à *évaluer des expressions*,
mais que sont ces fameuses « expressions » ? Nous allons commencer à le
découvrir dans la suite de ce chapitre.

### Saisir un nombre

Vous avez pu voir juste au-dessus que Python n'aime pas du tout les suites de
lettres qu'il ne comprend pas. Par contre, non seulement il comprend très bien
les nombres, mais en plus, il les adore !

```python
>>> 42
42
```

Vous pouvez même saisir des nombres à virgule, regardez :

```python
>>> 13.37
13.37
```


> **On utilise ici la notation anglo-saxonne, c'est-à-dire que le point remplace
la virgule. La virgule a un tout autre sens pour Python, que nous découvrirons
plus loin.**

En programmation, ces nombres à virgules sont appelé des **flottants**. Ils ne
sont pas représentés de la même façon dans la mémoire de l'ordinateur que les
nombres entiers. Ainsi, même si leurs valeurs sont égales, sachez que `5` n'est
pas tout à fait la même chose que `5.0`.

Il va de soi que l'on peut tout aussi bien saisir des nombres négatifs.
Essayez. ;)

D'accord, ce n'est pas extraordinaire. On saisit un nombre et Python le
répète : la belle affaire ! Néanmoins, ce n'est pas aussi inutile que vous
pourriez le penser. Le fait qu'il nous renvoie une valeur signifie que Python a
bien compris **la forme** et **le sens** de ce que vous avez saisi. Autrement
dit, cela signifie que *les expressions* que vous avez tapées sont **valides**
dans le langage Python, donc que vous pouvez utiliser cette console pour
vérifier la validité d'une expression en cas de doute.

> **Un peu de vocabulaire :**
>
> L'ensemble de règles qui déterminent *la forme* des expressions acceptées par
> un langage de programmation
> constitue la **syntaxe** de ce langage. *Le sens* de ces expressions, quant à
> lui, est déterminé par sa **sémantique**.

Nous avons maintenant un première observation à retenir : les nombres, tout
comme les chaînes de caractères (`"Bonjour"`), sont des expressions valides en
Python. Ces expressions désignent **des données** que l'on peut manipuler dans
ce langage.

### Opérations courantes

Maintenant que nous savons que Python comprend les nombres, voyons un peu ce
qu'il est capable de faire avec.

#### Addition, soustraction, multiplication, division

Pour effectuer ces opérations, on utilise respectivement les symboles `+`, `-`,
`*` et `/`.

```python
>>> 3 + 4
7
>>> -2 + 93
91
>>> 9.5 - 2
7.5
>>> 3.11 + 2.08
5.1899999999999995
```

> *Pourquoi le dernier résultat est-il approximatif ?*

Python n'y est pas pour grand chose. En fait, cela vient de la façon dont les
nombres flottants sont représentés dans la mémoire de votre ordinateur. Pour
que tous les nombres à virgule aient une taille fixe en mémoire, ceux-ci sont
représentés avec un nombre limité de chiffres significatifs, ce qui impose à
l'ordinateur de faire des approximations parfois un peu déroutantes.

Cependant, vous remarquerez que l'erreur (à 0.000000000000001 près) est infime
et qu'elle n'aura pas de gros impact sur les calculs. Les applications qui ont
besoin d'une précision mathématique à toute épreuve peuvent pallier ce défaut
par d'autres moyens. Ici, ce ne sera pas nécessaire.

Faites également des tests pour la multiplication et la division : il n'y a
rien de difficile.

#### Division entière et modulo

Si vous avez pris le temps de tester la division, vous vous êtes rendu compte
que le résultat est donné avec une virgule.

```python
>>> 10 / 5
2.0
>>> 10 / 3
3.3333333333333335
>>>
```

En d'autres termes, quelles que soient ses opérandes, la division de Python
donnera toujours son résultat sous la forme d'un flottant. Il existe deux
autres opérateurs qui permettent de connaître respectivement le résultat d'une
*division euclidienne* et le reste de cette division.

La division euclidienne, c'est celle que vous apprenez à poser à l'école.
Rappelons rapidement sa définition : la division euclidienne de $a$ par $b$ est
l'opération qui consiste à trouver le *quotient* $q$ et le *reste* $r$ tel que
$0 \le r < b$, vérifiant :

$$a = q \times b + r$$

L'exemple ci-dessous montre que la division euclidienne de $10$ par $3$ a pour
quotient $3$ et pour reste $1$. Soit $10 = 3 \times 3 + 1$.

```
    10 | 3
       +---
     1 | 3
       |
```

L'opérateur permettant d'obtenir le quotient d'une division euclidienne est
appelé « division entière ». On le note avec le symbole `//`.

```python
>>> 10 // 3
3
```

L'opérateur `%`, que l'on appelle le « modulo », permet de connaître le reste
de cette division.

```python
>>> 10 % 3
1
```

#### Puissance

Si vous êtes curieux, vous avez probablement déjà essayé de calculer une
*puissance* avec Python, de la même façon que vous auriez utilisé une
calculatrice. Sur cette dernière, vous vous souvenez certainement que
l'opérateur de puissance correspond à la touche "`^`". Essayons !

```python
>>> 3 ^ 2
1
```

En voilà, un résultat bizarre. Tout le monde sait bien que $3^2 = 9$ ! o_O

Rassurez-vous. Python le sait également. C'est simplement que l'opérateur `^`
ne désigne pas une puissance pour lui, mais une toute autre opération qui porte
le nom barbare de « XOR bit-à-bit » et que vous pouvez vous empresser d'oublier
pour le moment.

L'opérateur de puissance, quant à lui, se note `**`. Regardez :

```python
>>> 3 ** 2
9
```

Vous pouvez même vous en servir pour calculer une puissance qui n'est pas
entière. Par exemple, une racine carrée (rappelez-vous que $\sqrt{x} =
x^{\frac{1}{2}}$) :

```python
>>> 25 ** (1/2)
5.0
```

Notez que le résultat nous est donné sous la forme d'un nombre à virgule,
puisque l'un des deux opérandes, `1/2`, n'est pas une valeur entière.

Tout cela nous amène à deux nouvelles observations. La première, c'est qu'en
plus des nombres, les expressions mathématiques sont également des expressions
valides en Python.

La seconde, c'est que votre nouvel ami serpent est un génie en calcul mental.
Cela n'a rien d'étonnant ; souvenez-vous que la principale fonction d'un
programme (donc d'un langage de programmation) est de nous permettre à nous,
humains, de faire faire des calculs à un ordinateur. En fait, pour lui, *toute
instruction est un calcul à effectuer*, y compris, évidemment, les petites
opérations de calcul mental que nous venons de lui soumettre.

## En résumé

Récapitulons ce que nous avons appris dans ce premier chapitre.

- L'invite de commandes Python permet de tester du code au fur et à mesure
  qu'on l'écrit.
- Python est capable d'effectuer des calculs, exactement comme une
  calculatrice.
- Un nombre décimal s'écrit avec un point et non une virgule. Les calculs
  impliquant des nombres décimaux donnent parfois des résultats approximatifs.
- Python différencie la *division réelle* (`/`) de la *division euclidienne*
  (`//` et `%`).

Plus important encore, en termes de vocabulaire :

- Les chaînes de caractères (comme `"Salut !"`) et les nombres sont des
  **expressions valides** en Python.
- La forme des expressions acceptées par un langage de programmation est sa
  **syntaxe**.
- Le sens que donne le langage aux expressions qu'il accepte est sa
  **sémantique**.

Bien entendu, Python est bien plus qu'une simple calculatrice. Vous allez très
vite vous en rendre compte dans les prochains chapitres.
