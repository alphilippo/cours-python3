# Booléens et branchements conditionnels

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

## Vrai ou faux ?

