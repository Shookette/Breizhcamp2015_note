# ES6 dès aujourd'hui avec BabelJs
# Grégory Houiller

# ES6 c'est quoi
    Nouvelle version de ES avec de nouvelles API et syntaxe
    Plus productive et plus expressif

# Influence
    CoffeeScript
        * Classes
        * Arrow Functions
        * Rest+Spread

    NodeJS
        * Dynamisation de l'écosystème JS
        * Module CommonJs

# Babel
    Transpiller > Transforme code ES6 en ES et interprétable sous IE9+ / FF19+ / CH23+

## Ce que çà fait
    Parse code ES6
    Transforme AST (Abstract Synthax Script)
    Genere du ES à partir de AST

## Démarer
    * Comme plugins
        --* Gulp
        --* Grunt
        --* Browserify

## Debugger avec Babel
    * Browserify
    * Babblify
    * Watching


# ES6

## Classes
### Apport

    * Juste du sucre synthaxique
    * Simplifier la déclaration, pas de nouveauté direct
    * Héritage plus simple avec le système de classe offert par ES6

### Limitation

    * Pas de propriété Static
    * Attention à la chaine de résolution des prototypes de hoisting (phase particulière dans l'interprétation de ES)

## Arrow Functions
### Apport

    *
    * Binder sur le contexte appelant

### Limitation

    * Ce ne sont pas de constructeurs
    * Les fonctions .apply et .bind ne change pas

## Modules
### Apport

    * Export
    * Import / possibilité de créer des alias lors de l'import
    * Mixin

### Limitations

    * Nécessite encore un contexte CommonJs (NodeJs / Browserify, webpack ...) Même avec Babel


## Template Strings
### Apport

    (Alt-Gr 7) = `

    * nouveau délimiteur évitant les problèmes entre les ' et les "
    * Possibilité d'importer directement des variables dans ce délimiteur
    * Support chaînes multilignes
    * très performant

### Limitations

    * null

## Object Literals
### Apport

    * Seulement du sucre synthaxique

### Limitations

    * null

## Rest, Spread, Default
### Apport

    * Rest :  grâce à là chaîne '...arg' permet de passer autant de paramètre dans une fonction et sera traduit en tableau
    * Spread :  permet lors de l'appel d'une fonction de passer un tableau et de le passer directement a la fonction
    * Default : Permet de définir les valeurs par défault

### Limitations

    * Pas aussi puissant que CoffeeScript
    * Rest : peut seulement être passé au début ou à la fin d'une fonction pas entre 2


## Destructuring
### Apport

    * Permet de récupérer des valeurs / paramètre à partir d'un objet plus facilement
        --* { top, right, left, bottom} = objet permet de récuper les variables top / right / left et bottom défini dans l'objet
    * Permet de définir et passer des objets directement en paramètre d'une fonction
        --* Peut se cumuler avec Default afin de définir une valeur par défaut dans notre objet

### Remarques

    * Vraiment intégré dans les modules

## Generators
### Apport

    * Ajoute les iterators avec JS


## Block declaration
### Apport

    * Let : permet de définir une variable / function seulement pour le block actuel
    * Const : Permet de définir des variables en Read-Only (niveau référence)
    * Function declaration : porté > block

## Autre nouveauté

    * Promise : Permet d'éviter les appel de callbacks en cascade
    * Set / Map / WeakMap : Permet d'intégrer des dictionnaires en JS
        --* Map : Dictionnaire de données
        --* WeakMap : Map ou les clés sont des objets
        --* Set : Permet d'insérer des données en gardant l'unicité
    * Symbol : permet de définir du pseudo-privé
    * Proxy : Permet de surcharger partiellement une fonction / AOC >  ex : transformer le return d'un get pour retourner des données supplémentaire.
    
