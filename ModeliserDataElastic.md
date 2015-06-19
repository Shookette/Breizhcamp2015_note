# Comment *(ne pas réussir à)* modéliser ses data dans ElasticSearch !
## Bruno Bonnin

# Context
    * Beaucoup de données
    * Différent type de données
    * Différent système pour gérer tout ça
        --* Personnes
        --* Contrats
        --* LDAP
        --* TEL

    eviter la séparation
        Mettre les données dans un puits (ElasticSearch) pour tout rassembler
        Puis après les receuillir via des Search-Based Apps


LogStash (récupération de log)> ElasticSearch (base) > Kibana (dashboard)


# Question à se poser
    * Les usages ? Partiellement connus
    * Quelles données ? Toutes (ou presque), en tout cas le maximum possible !
    * Des contrats techniques

# Mise à jour du puits
    * Batch > simple style cron
    * Fil de l'eau  > JMS

# Quels modéle pour ElasticSearch
    * "La Brute" : Un seul type de document (tout en nested)
        --* Contient plusieurs tables, ou des informations de différent utilité / tables
        --* Obligé de jouer avec les nested à la fois pour le stockage que pour la requête
        --* Avantages :
            ----* Récupérer l'ensemble des données directement
        --* Désavantage :
            ----* Mise à jour : Temps de re-indexation / complexité
            ----* Vue orienté 1 usage

    * "Le Truand" : Un doc par objet source /Base / Type
        --* Simple à mettre en place
        --* Permet de répondre à plusieurs cas d'utilisation
        --* Plus dur de récupérer des données dispatché
        --* Requête imbriqué afin d'obtenir plus de données
        --* Avantages :
            ----* Facile à mettre à jour
        --* Désavantage :
            ----* Requêtage (plusieurs requête pour tout reconstruire)

    * "Le Bon" : Faire un mix nested et parent / child
        --* Lors de l'indexation d'un document enfant on indique sont parent lié
        --* Permet lors du mapping de déclarer grace à *_parent* le type du parent associé
        --* Puis dans la requête on spécifie le parent *?parent=XXXX*
        --* Type de requête has_child / has_parent afin de récupérer les données soit de l'enfant soit du parent
        --* Nouveau depuis 1.5 > inner_hits permet de récupérer les données qui match les critère spécifié pour l'enfant et le parent
        --* Avantages :
            ----* Modèle permettant de répondre à la plupart des usages
            ----* Séparation de documents ayant des cycles de vie différents
            ----* Avec inner_hits, capacité à retrouver des documents liés entre eux Facilement
        --* Désavantage :
            ----* Requête plus lentes pour les documents liés par un lien parent / enfant (3/4 x plus lent que les requêtes normal)
            ----* ElasticSearch met en mémoire la table des liens (prévoir assez de mémoire pour ElasticSearch)


difficile de modéliser les données

# Résumé
    * Penser "usages" primordial !
    * Utiliser les nested documents pour des données ayant un lien fort, avec le même cycle de vie
        --* Ne pas hésiter à dupliquer
    * Utiliser les lieins parents/enfants sur les documents pouvant vivre indépendamment les uns des autres.
        --* Requêtes avec "inner_hits" permet de resortir à la fois le parent et l'enfant pour une même requête
    * Tenir compte des contraintes techniques de votre env
