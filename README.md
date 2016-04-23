# Python 3 pour l'apprenti sorcier

Ce dépôt héberge temporairement les sources du cours « *Python 3 pour l'apprenti
sorcier* », destiné à devenir le cours Python de référence du site [Zeste de
Savoir](http://zestedesavoir.com).

Toute remarque de fond est évidemment la bienvenue.

## Installation

Assurez-vous d'avoir Python et virtualenv installés sur votre machine.

    $ git clone git@github.com:ArnaudCalmettes/cours-python3-poo.git
    $ cd cours-python3-poo
    $ sudo apt-get install python3 python3-virtualenv
    $ virtualenv -p python3 venv
    $ source venv/bin/activate
    $ pip install -r requirements.txt

Pour compiler le tutoriel :

    $ make html

Ceci génère le tutoriel au format html dans le répertoire `_build/html`.
Pour la liste des formats supportés par Sphinx, tapez `make`.

