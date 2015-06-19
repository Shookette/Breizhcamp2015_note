#Angular2 le reveil de la force
## Grégory Houllier & Nicolas Pennec

# Angular 1
    What's
        * Single Page application
        * DataBinding (bidirectionnel)
        * Scope
        * Injection dépendance

# Angular 2
    New langage AtScript > TypeScript

##Philosophie
    2-way data-binding
    Baser sur les futurs standars
        * WebComponents
        * ES6 / ES7 / TypeScript
        * EverGreen Browser (browser toujours mis à jours FF / chrome)
    Boost Perf

    TypesScript > Typage
    Transpiller > Traceur (de google TypesScript vers ES5)
    TypesScript permet de faire du ES5/6/7
        Annotation ES7
        Class / Arrow Function ES6

## Production Ready
    NO !
    ANgular 2 > developer preview
    Pas stable
    Pas de roadmap
    Doc en cours
    version alpha mis à jour toute les semaines / 2 semaines

## PoC Ready
    YES !

## What's changed
    Angular2 :
        * Plus de controller
        * Plus de service
        * Plus de module
        * Plus de Scope
        * plus de JQlite
        * Directive reste
        * Dependency Injection (TypesScript)
        * New Component
        * New classes with ES6

    Directive :
        Permet d'etendre le DOM (add comportement mouse hover / click)

    Component pour les effets visuel et plus les directives

## How use it
    Import Traceur (transpiller)
    Import JSpm
    Import Angular2

        Angular1 > ngApp / ici
## Component

### Component - Template
    html juste à appeler le component comme une balise
    TypeScript
        * Import component
        * Import View
        * Component > declare selector : "Name" > name of the future balise
        * View > declare template : "html" > effets de l'appel de la balise

    Scope > Devient l'instance de notre component

### Directive - DOM
    TypeScript
        * Import Directive
        * Define Selector : '[balise]'
        * Define

### Templating
    Property binding declare with [] like [model]="message"
    Event binding declare with () like (click) = "hello(message)"

#### Whole template
    replace ngIf / ngElse with  
        > `<div *if=""`

## Dependency Injection
    in declare of component add injectables array
        > `injectables: [MyService]`

# Migration 1.X vers 2.X
    * Commencer par coder en ES6 / TS puis le transpiller
    * Module ES6 pour structurer son code
    * Utiliser le NgNewRouter dispo en 1.5 (quand ??)
        --* Router associé component
    * Préférer la syntaxe "controllerAs" et "bindToController" pour les directives
        --* Ne pas déclarer les propriété dans le Scope
        --* Déclarer dans le controller
        --* Pas d'accroche sur le scope qui n'est plus supporter
