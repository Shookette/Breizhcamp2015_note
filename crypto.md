#Cryptographie
##ZenData
    actualy > donné non crypté http pas d'auth
    code d'erreur très verbeux > pouvoir comprendre
        * executer à l'intérieure d'une bdd temps de réponse élevé
        * nature fullstack ne gère pas comme il devrait la sécurité
        * limité les requête / demande inutile sur le backend avec le front
            --* crypto peut permettre d'aider à bloquer les requêtes inutiles avant
        * toolbox
            --* AES 256 BIT >
            --* hash crypto > permet de gérer proprement ces valeurs car si alterné alors resultat totalement différent
                ----* temps réponse début de la taille du fichier / de la demande / du type d'hash
                ----* besoin d'un salt pour pouvoir hash correctement
                    ----* pb > salt = clé secrête > elle doit rester secrête car si intércepté alors tout le hashage compromis
                    ----* taille du salt variable > min 128 bit > pouvant être en préfixe / suffixe ou en zigzag encoding (salt appliqué partout dans le hashage)
                    ----* OSS > serveur de clé (public / privé)
                        ------* shamir algorithm

# API
    accessToken > associé requête à un utilisateur (machine / user)
        * hash > de l'accessToken (init > salt + clé)
    associé un compte à une clé unique pour le distingué (clé créée à partir d'un hashage du compte (hash à partir d'un salt du accessToken))
    hash à partir de l'accessToken + ancien hashage
        ["", AES]

        OTP créer à partir de HOTP (SecretKey, TC)
                                    > hash

        possibilité de faire tomber accessToken si un hackage reperé afin de stopé la possiblité d'executer des requêtes.
            > à partir d'un mauvais hachage etc

        cas 2 grande possibilité

            value (ex rib) > hash > key

        SSL pas suffisant > car ne detecte pas tout les bruits
            > le hashage permet de détecter plus facilement les possibles attaques pour après pouvoir mieux les gérer

            exemple > envoie de l'email
                > si envoie de 12 demande > 1 validé les 11 autres disable
                    > souvent à duré données
                > possibilité d'appliquer le hashage à tout le niveau

                > encodage import niveau perf car coup en allocation mémoire et envelopper dans AES peut avoir des grosses perte de perf


        Mettre à jour une application Legacy très compliqué et lourd niveau refactoring car certainne clé était prévu pour être dans de l'affichage form etc

        Réserver l'encapsulation AES (hashage etc) pour un projet fromscratch
