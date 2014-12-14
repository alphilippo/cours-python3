# Des noms et des objets

> *Brisingr* signifie *feu*. C'*est* le feu. La chose est le mot. Connais le
> mot, tu domineras la chose.

> *Brom -- Eragon (Twentieth Century Fox, 2006)*

C'est l'un des principes fondamentaux de la magie comme de la programmation :
nommer quelque chose, c'est le contrôler. Quand on écrit un programme, on
manipule des **objets** (des *choses* abstraites) en leur donnant des **noms**.
C'est la base, la première notion essentielle que vous devez maîtriser pour
~~jeter des sorts~~ programmer.

Dans ce chapitre, nous allons apprendre :

* à nommer les objets pour les manipuler,
* que tous les objets ne sont pas de la même nature,
* que certains objets représentent des *données*,
* que d'autres sont des *actions*.

## Les variables

### Des étiquettes pour s'y retrouver

En Python, une variable n'est rien d'autre qu'un **nom** que l'on donne à un
objet pour se souvenir de lui et le manipuler. Regardez :

```python
>>> x = 40
>>> x
40
```

Dans cet exemple, j'ai créé une variable `x` à laquelle j'ai *affecté* la
valeur `40`, puis j'ai demandé à Python de me donner la valeur de `x`, et
celui-ci m'a retourné `40`. À partir de maintenant, je peux utiliser le nom `x`
dans toutes les expressions où j'aurai besoin de ce nombre :

```python
>>> x + 2
42
>>> x * 3
120
```

*Mais pourquoi est-ce qu'on appelle ça une variable ?* me demanderez-vous à
juste titre.

Eh bien parce que les données qu'elles désignent ne sont pas *fixes*.
Contrairement à la chaîne `"Bonjour"` ou au nombre `40` (que l'on appelle, par
opposition, des *constantes*) la valeur d'une variable peut changer au cours de
l'exécution du programme : elle est... variable, quoi. Autrement dit, `"Paris"`
sera toujours `"Paris"`, mais `rien` n'est jamais figé dans le marbre. ;)

Par exemple, rien ne m'empêche de décider que `40`, c'est nul, et que `x`
ferait mieux de désigner le nombre `25` ou la chaîne `"Salut"`. Python se
contentera de changer docilement la valeur associée à ce nom.

```python
>>> x = 25
>>> x
25
>>> x = "Salut"
>>> x
'Salut'
```

> __Il faut voir une variable en Python **comme une simple étiquette**, un
*post-it* sur lequel on écrit un nom et que l'on peut coller sur un objet,
comme ça nous chante, quitte à le décoller plus tard pour le coller sur autre
chose.__

De nombreux cours de programmation choisissent de présenter les variables comme
des *boîtes* dans lesquelles on peut ranger des valeurs : si c'est l'image que
vous avez en tête, **chassez-la immédiatement de votre esprit** ! C'est une
bonne analogie pour certains langages de programmation, mais pas ici. En
Python, une variable n'est vraiment qu'*un nom* attaché à quelque chose.
Contrairement à une boîte qui a nécessairement un volume (qu'elle soit vide ou
non), vous pouvez considérer qu'une variable de Python ne prend (presque) pas
de place dans la mémoire de votre ordinateur : que vous la colliez sur une
souris ou sur un éléphant, une étiquette aura toujours la même taille
négligeable.

Nous aurons l'occasion de revenir sur cette histoire d'étiquettes (ou
*références*) dans un autre chapitre. En attendant, gardez bien cette métaphore
en mémoire *et ne me parlez plus jamais de boîtes !*

> *D'accord, une variable est une étiquette que l'on colle sur les choses pour
leur donner un nom, mais... c'est tout ? Ça ne sert _qu'à ça_ ?*

En effet, ça ne sert qu'à « ça », mais ce « ça » est beaucoup plus important
que ce que vous imaginez. En donnant un nom à un objet, vous demandez à Python
de *se souvenir de lui*. Littéralement. Vous lui ordonnez de le garder bien au
chaud dans un coin de sa mémoire. Ce n'est pas anodin du tout !

**Tant qu'un objet est affecté à une variable, celui-ci reste accessible à
Python : on dit qu'il est *référencé*.** Et l'inverse est vrai également : si
un objet n'est référencé par aucune variable, alors Python se donne le droit de
l'oublier en l'effaçant de sa mémoire. C'est exactement comme quand vous prenez
le train :

> *Nous vous demandons d'étiqueter convenablement tous vos bagages. Tout colis
> ou objet abandonné sera systématiquement détruit.*[^gare]

[^gare]: Annonce en gare de la SNCF

En résumé : si vous comptez utiliser un objet, nommez-le !

### Un peu de syntaxe

Ce simple mécanisme de *nommage* est tellement utilisé en Python que celui-ci
propose un certain nombre de raccourcis pour définir, modifier ou supprimer des
variables.

Comme nous venons de le voir, on affecte un objet à une variable en utilisant
le symbole `=`.
```python
>>> langage = "Python"
```

Ce symbole, dans le jargon des programmeurs, on l'appelle *l'opérateur
d'affectation*. On peut aussi s'en servir pour affecter simultanément plusieurs
valeurs à plusieurs variables, pour peu que celles-ci soient séparées par des
virgules :

```python
>>> langage, version = "Python", 3.4
>>> langage
'Python'
>>> version
3.4
```

Si l'on souhaite affecter une seule valeur à plusieurs variables en même temps,
on peut même chaîner les affectations, comme ceci :

```python
>>> x = y = 0
>>> x
0
>>> y
0
```

Notez que dans ce cas, nous avons simplement collé deux étiquettes sur le même
objet. Si on en déplace une, l'autre ne sera pas impactée.

Enfin, si vous souhaitez supprimer purement et simplement une variable, vous
pouvez utiliser le mot-clé `del` pour demander à Python de l'oublier.

```python
>>> prenom = "Clem"
>>> prenom
'Clem'
>>> del prenom
>>> prenom
Traceback:
    ...
NameError: name 'prenom' is not defined
```

> __Notez bien que `del`, dans ce contexte, sert à supprimer une *variable*, mais
pas forcément l'objet qu'elle référence.__

La différence c'est que si plusieurs variables pointent sur le même objet, la
suppression de l'une d'entre elles n'affectera pas les autres :

```python
>>> a = b = 1
>>> b
1
>>> del b
>>> a
1
```

Voilà qui devrait suffir en ce qui concerne les affectations. Et si nous nous
intéressions maintenant à ces fameux objets que vous venez d'apprendre à
nommer ?

    TODO : passer ce qui suit dans un paragraphe sur les conventions de nommage.

> __Certains mots-clés de Python sont *réservés*, c'est-à-dire que vous ne
pouvez pas créer des variables portant ce nom.__

En voici la liste pour Python 3 :

+----------+---------+--------+----------+-------+
|`and`     |`del`    |`from`  |`none`    |`true` |
+----------+---------+--------+----------+-------+
|`as`      |`elif`   |`global`|`nonlocal`|`try`  |
+----------+---------+--------+----------+-------+
|`assert`  |`else`   |`if`    |`not`     |`while`|
+----------+---------+--------+----------+-------+
|`break`   |`except` |`import`|`or`      |`with` |
+----------+---------+--------+----------+-------+
|`class`   |`false`  |`in`    |`pass`    |`yield`|
+----------+---------+--------+----------+-------+
|`continue`|`finally`|`is`    |`raise`   |       |
+----------+---------+--------+----------+-------+
|`def`     |`for`    |`lambda`|`return`  |       |
+----------+---------+--------+----------+-------+

Ces mots-clés sont utilisés par Python, vous ne pouvez pas construire de
variables portant ces noms. Vous allez découvrir dans la suite de ce cours la
majorité de ces mots-clés et comment ils s'utilisent.

## C'est l'histoire d'un type...

Jusqu'à maintenant, nous avons joué rapidement avec des données toutes simples
(`42`, `"Bonjour"`), et depuis le début de ce chapitre, je vous parle de ces
données comme étant des *objets* sur lesquels on peut coller des étiquettes.

La notion d'*objet* en programmation est assez vaste, et c'est la raison pour
laquelle vous en découvrirez les détails de façon progressive, à mesure que
nous avancerons dans ce cours. Vous vous apercevrez bientôt qu'en Python,
*tout* est considéré comme un objet, mais l'idée que je voudrais que vous
gardiez en tête pour le moment c'est que **les objets sont les choses que l'on
manipule dans un programme**.

Et la première caractéristique d'un objet, c'est son **type**. On parle
également de « type de données ».

### Plusieurs types de données

Vous serez d'accord avec moi si je vous dis qu'une éponge et un tournevis ne
sont absolument pas la même chose. Pourtant, ce sont deux objets, non ? Eh bien
en programmation, on dira que ce sont deux objets *de types différents*.

Comme le dit le dicton, *on ne peut pas additionner des choux et des carottes*
et *on ne mélange pas les torchons avec les serviettes*. Chaque objet porte un
*type* qui caractérise la façon dont on peut l'utiliser : vous imaginez bien
qu'on ne fera pas les mêmes choses avec le nombre `42` qu'avec la chaîne `"Je
mange des ours"`.

> __Le type d'un objet, c'est ce qui définit ses caractéristiques : à quoi il
ressemble, comment on l'utilise, à quoi il sert... bref, ce qu'il *est*.__

Jusqu'ici, vous avez croisé des objets de trois types différents. Prenons le
temps de les examiner de plus près, si vous le voulez bien.

#### Les nombres entiers

Nous l'avons vu au chapitre précédent, Python fait la différence entre les
nombres entiers et les nombres à virgule. Un nombre entier, c'est donc un
nombre *sans virgule*, comme `3`, `920000` ou encore `-12`. Ces nombres, Python
les appelle des `int`. Il s'agit de l'abréviation de *integer* (le mot anglais
pour *nombre entier*). En français, nous nous contenterons de les appeler « des
entiers ».

Étant donné que nous avons déjà passé en revue les opérations que l'on peut
appliquer sur ces nombres, nous n'allons pas les répéter ici.

Par contre, il peut être intéressant de savoir que Python accepte plusieurs
notations pour désigner des entiers. Si les notions de *notation binaire* ou
*hexadécimale* ne vous disent rien, vous pouvez sauter le paragraphe suivant.

> Dans beaucoup de langages de programmation, les nombres peuvent être
> représentés selon différents systèmes de numération.
>
> Par exemple, on peut les noter sous leur forme binaire en préfixant la valeur
> de `0b` :
>
> ```python
> >>> 0b10
> 2
> >>> 0b11
> 3
> >>> 0b101010
> 42
> ```
>
> Ou bien selon la notation hexadécimale, avec le préfixe `0x` :
>
> ```python
> >>> 0x10
> 16
> >>> 0xff
> 255
> ```
>
> Ou encore en octal en utilisant le préfixe `0o`:
>
> ```python
> >>> 0o10
> 8
> >>> 0o755
> 493
> ```
>
> `
> Python comprendra tous ces nombres comme des entiers. Seule la notation
change, pas leur type.

Enfin, si vous savez déjà programmer dans un autre langage, il est possible que
vous vous demandiez quelles sont *les bornes* (les valeurs minimale et
maximale) des entiers. Sachez qu'en Python, les entiers ne sont pas bornés :
tant que vous disposez de suffisamment de mémoire pour les faire tenir dedans,
Python est capable de représenter des entiers indéfiniment grands ou petits.

Vous ne me croyez pas ? Eh bien, demandez-lui donc de calculer
`123456789 ** 500` ; vous verrez si je vous raconte des bobards !

#### Les nombres flottants

Les « flottants » sont des nombres à virgule, comme `3.1416` ou `-169.8`.
Python les appelle des `float`. D'emblée, on peut se demander quel peut bien
être le rapport entre un nombre et le fait de *flotter*. Eh bien ce qui flotte,
c'est justement la virgule : la véritable appellation de ces nombres est
« nombres à virgule flottante ».

Je vous ai dit plus tôt que ces nombres sont limités à une taille fixe en
mémoire (64 bits sur la plupart des ordinateurs). Imaginons que cela
corresponde à 16 chiffres significatifs, même s'il s'agit d'une très grossière
approximation de la réalité. Comment faire, dans ce cas, pour représenter un
nombre positif supérieur à 10^16^ ou inférieur à 10^-16^ ? Eh bien l'idée,
c'est qu'une partie de la donnée sert à décrire où se trouve la virgule (la
*puissance de dix* du nombre, son *exposant*) alors que le reste nous donne les
16 chiffres significatifs (qui forment la *mantisse*[^mantisse] du nombre).

[^mantisse]: Si vous trouvez que ce mot n'est pas très joli, figurez-vous qu'on
peut faire encore bien pire que ça ! En effet, une norme internationale
préconise l'utilisation du terme *significande* à la place de *mantisse*…

En somme, pour représenter les nombres `123.0`, `1230000.0` et `0.00000123`,
votre ordinateur se contente de déplacer la virgule vers la droite ou la gauche
en faisant varier l'exposant, tout en gardant une mantisse identique. C'est
parce que cette virgule se déplace "toute seule" en fonction de l'ordre de
grandeur du nombre qu'on la qualifie de *flottante*.

Cette façon de représenter les nombres décimaux n'est pas propre à Python :
elle est encodée dans le microprocesseur de votre ordinateur. Elle lui permet
d'effectuer des calculs extrêmement rapidement, avec une précision imparfaite,
certes, mais plus que correcte sur des nombres arbitrairement grands ou petits.
Cela dit, pour votre culture, sachez que Python propose également dans sa
bibliothèque standard un type de données qui permet de représenter les nombres
décimaux avec une précision réglable et extrêmement fine. Nous n'en parlerons
pas dans ce cours, mais sachez que ça existe !

#### Les chaînes de caractères

Il n'y a pas que les nombres dans la vie, il y a le texte aussi ! Et ce texte,
on le représente en Python dans des objets qu'il appelle des `str`.

> _Des *streuh* ? C'est quoi un *streuh* ?_

C'est l'abréviation du mot *string* (ne rigolez pas !), que l'on peut traduire
par *chaîne* dans ce contexte, sous-entendu *chaîne de caractères*.

Comme nous l'avons déjà vu, on peut créer une chaîne de caractères en plaçant
le texte entre guillemets doubles, comme ceci : `"Salut, Python !"`. Toutefois,
c'est loin d'être la seule façon de les écrire. Imaginez que vous ayez besoin
que votre chaîne *contienne* des guillemets, comment s'y prendre ?

Pour cela, vous avez deux solutions. La première et... la seconde.

La première, c'est d'entourer votre texte de *guillemets simples*
(l'*apostrophe* `'` sur votre clavier), comme ceci :

```python
>>> '"Diantre !" dis-je.'
'"Diantre !" dis-je.'
```

Remarquez que c'est exactement sous cette forme que la console Python vous
retourne le résultat.

La seconde solution, c'est d'*échapper* les guillemets contenus dans la chaîne,
en utilisant le symbole *anti-slash* (`\`), comme ceci :

```python
>>> "\"Diantre !\" dis-je."
'"Diantre !" dis-je.'
```

Ce symbole `\` sert à introduire un caractère spécial dans les chaînes. Ici,
les guillemets ont ceci de spécial qu'ils *ne servent pas à délimiter une
chaîne*. C'est exactement la même chose lorsque vous souhaîtez échapper une
apostrophe dans une chaîne délimitée par des guillemets simples :

```python
>>> 'Python, c\'est coolympique !'
"Python, c'est coolympique !"
```

Regardez la réaction de Python sur le dernier exemple. Pour éviter d'échapper
l'apostrophe, il a choisi de délimiter la chaîne avec des guillemets doubles,
pour une fois. *Essayez de le piéger en saisissant une chaîne qui contient
à la fois des guillemets et des apostrophes, pour voir.*

Notez également que l'anti-slash est lui-même un caractère spécial : pour
l'incorporer dans une chaîne, il faut parfois l'échapper, même si Python est
assez intelligent pour se rendre compte quand ce n'est pas nécessaire.

```python
>>> "ceci \ est un anti-slash"
'ceci \\ est un anti-slash'
>>> "je vous offre un anti-slash: \"
  File "<stdin>", line 1
    "je vous offre un anti-slash: \"
                                   ^
SyntaxError: EOL while scanning string literal
```
```python
>>> "je vous offre un anti-slash: \\"
'je vous offre un anti-slash: \\'
```

> *Et si je veux écrire une chaîne qui fasse plusieurs lignes ?*

Pour cela, vous avez encore deux alternatives. La première et... d'accord,
j'arrête avec cette blague. 

La première alternative, c'est d'utiliser le caractère spécial `\n`, qui
représente un *retour à la ligne*.

```python
>>> "voici une chaîne\nsur plusieurs lignes"
'voici une chaîne\nsur plusieurs lignes'
```

> *Hé, mais ça marche pas !*

Si si, ça fonctionne. Regardez :

```python
>>> print("voici une chaîne\nsur plusieurs lignes")
voici une chaîne
sur plusieurs lignes
```

Nous verrons juste après à quoi sert ce "`print`". Remarquez simplement que
l'affichage correspond bien à ce que nous voulions.

La seconde alternative, c'est d'entourer notre chaîne avec des *triples
guillemets* (`"""`) ou des *triples apostrophes*.

Essayons : 

```python
>>> """voici une chaîne
... sur plusieurs lignes"""
'voici une chaîne\nsur plusieurs lignes'
```

Les trois points (`...`) qui s'affichent dans cet exemple sont un indice visuel
de la console Python qui signifient que la saisie n'est pas terminée, et
qu'elle attend que je poursuive celle-ci sur une nouvelle ligne. Ici,
j'ai tapé `"""voici une chaîne`, `<Entrée>`, `sur plusieurs lignes"""`.

Si vous utilisez la console IDLE, ces trois points n'apparaîtront pas. Ne soyez
donc pas dérouté par la différence d'affichage avec les exemples du cours.

### D'autres types d'objets

Juste un peu plus haut, je vous ai montré un exemple bizarre où j'ai écrit
`print('une chaîne')`. Qu'est-ce que c'est que ce `print` ?

La première observation que l'on peut faire, c'est que `print` est un nom que
Python reconnaît :

```python
>>> print
<built-in function print>
```

Ce que l'interpréteur vient de répondre, c'est que `print` est une *fonction*.
C'est-à-dire un objet qui sert à *faire quelque chose*.

Pour utiliser une fonction, il faut l'*appeler*. Pour cela, il faut accoller des
parenthèses après son nom :

```python
>>> print()

>>>
```

> *Mais... il ne s'est rien passé ?!*

Si si, regardez plus attentivement : Python a sauté une ligne. En fait, l'appel
`print()` affiche une ligne vide. Essayons autre chose :

```python
>>> print("Bonjour !")
Bonjour !
>>> x = 2 + 2
>>> print("x =", x)
x = 4
``` 

Cette fois, nous avons passé *un argument* à la fonction `print` (la chaîne
`"Bonjour !"`), et le résultat affiché est le contenu de cette chaîne. Puis
nous lui avons passé deux objets (la chaîne `"x ="` et le nombre étiqueté par
la variable `x`) et celui-ci les a affichés à la suite.

Vous l'aurez deviné ; la fonction `print(...)` sert à afficher ses arguments à
l'écran. C'est d'ailleurs ce que signifie son nom : *imprimer* (sous-entendu
*imprimer à l'écran*, soit *afficher*).

> *Mais depuis le début on affiche des trucs à l'écran, il suffit de les taper
> dans la console pour ça !*

C'est vrai, sauf que nous n'allons pas utiliser le console *ad vitam aeternam*.
À un moment donné, nos programmes vont devenir plus compliqués, et nous devrons
les écrire dans des fichiers pour les exécuter hors de la console interactive.
Dans ce cas, nous utiliserons `print(...)` pour afficher des informations à
l'écran.

De plus, son comportement n'est pas tout à fait le même :

```python
>>> ma_chaine = "Je vous offre un anti-slash : \\"
>>> ma_chaine
'Je vous offre un anti-slash : \\'
>>> print(ma_chaine)
Je vous offre un anti-slash : \
```

Lorsque j'envoie `ma_chaine` à l'interpréteur, celui-ci affiche la
**représentation** de l'objet (c'est-à-dire la chaîne telle qu'on la tape pour
la créer), alors que si je l'affiche avec `print(ma_chaine)`, Python affiche
**le message** contenu dans la chaîne, en remplaçant les caractères échappés et en
supprimant les guillemets.
