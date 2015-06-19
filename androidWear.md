#Android Wear 101
##Cyril Motier
    * google developper expert
    * capitaine train

#Android Wear Why ?
Eviter les distractions
    Ex : Vouloir lire un message > récupérer son tel > ne pas faire autre chose après
Micro Interactions
    * réduire les Interactions


! handheld /= wearable

#Contextual
    * Avoir les bonnes informations au bon moments
##Context Helpers :
    * Time
    * Sensors : Pouvoir detecter quand il y a un changement dans nos interactions
    * Calendar : Interagir à partir de notre calendrier afin de diffuser les bonnes technologies
    * Activity : Pouvoir en fonction de nos activité déterminer au plus proche nos besoins
    * Identity : Pouvoir interconnecter plus facilement tout nos devices
    * Location
    * Devices
    * Google Play Services : Appli mise à jours sans toucher au socle du device

##Glanceable :
###The essential info in a blink of an eye

##Low Interaction
###Design for big gestures
    Use action or gesture instead click
    voice action
    swap gestures

#Android Wear Ecosystem
1 device - 1 OS
Pas de codes / ressources partagées

Pour pouvoir avoir un code partagé
    * Création d'un librarie permettant d'être utilisé sur les deux OS

##Pour communiquer
Play Services
Seulement si le téléphone le supporte
Données crypté

##Pour être installé
Dl un apply via le smarthphone
Qui contient une apply compatible android wear en APK
Un listener sur le tel qui écoute sur les apply installé si l'APK android wear existe dans l'apply installé, si oui alors installation sur le device android wear.

#Developping for android wear
##Notification
Si notre application actuelle utilise déjà le système de notification alors rien à faire car directement transmit sur le device android wear. Seul des améliorations de visibilité est nécéssaire afin de mieux recevoir / intercepter (visuellement) la notification.
Pour celà wearable extenders permet de modifier la notification reçu pour qu'elle soit plus compréhensible sur notre device android wear.

wearable extenders permet :
    * paginer
    * prioriser
    * trier

##Custom App
Android wear est dans la même ligné / utilisation qu'android de base
Android manager permet de gérer les imports si possible sur notre device


##Communiquer grâce à des API
    * NodeApi vérifie si des appareil / node connecté sont disponnible
    * MessageApi : Envoie des messsages au devices proche, si reçu tant mieux sinon tant pis
    * DataApi : Permet de synch automatiquement les devices proches
    * CapabilityApi : Demander les possibilités (Matériel) des devices proches

###DataApi
Intercepte les notifications grâce a des listener fournit par la DataApi permettant d'intercepter les events de modification et de suppression du téléphone sur le device


###Export
Avec gradle simple car juste une dépendance à rajouter en wearable


### Recap
    * Ne pas faire une apply pour android wear comme pour les smarthphone
    * Penser en forme de carte
    * Keep it simple
