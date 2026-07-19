# Actions on Objectives

## Définition

7e et dernière étape du Cyber Kill Chain. L'attaquant exécute enfin les actions planifiées
depuis le début de l'attaque. Il a dû réussir toutes les étapes précédentes pour arriver
jusqu'ici — c'est l'aboutissement de toute la chaîne.

## Côté attaquant (Adversary)

Les actions varient selon l'objectif et la motivation de l'attaquant (destruction, vol de
données, espionnage, extorsion...) :
- Chiffrer les fichiers via un ransomware
- Exfiltrer des informations/documents critiques
- Endommager le système en supprimant des informations critiques
- Élévation de privilèges pour étendre l'attaque à d'autres machines du réseau
- Collecter des identifiants pour accéder à d'autres appareils
- Collecter des informations dans le système
- Modifier/manipuler les informations du système

## Côté défenseur (Blue Team)

Les actions dépendent du scénario précis, mais la priorité absolue reste d'empêcher
l'exfiltration de données vers l'extérieur (l'un des impacts les plus fréquents aujourd'hui) :
- Détecter les anomalies dans le trafic réseau
- Restreindre et surveiller en continu l'accès réseau vers l'extérieur
- Restreindre et contrôler régulièrement l'accès aux fichiers/dossiers critiques
- Restreindre et surveiller l'accès aux bases de données contenant des infos critiques
- Utiliser des solutions DLP (Data Loss Prevention) pour empêcher les fuites de données
- Détecter les accès non autorisés

## Question de la leçon

**Q.** À quelle étape du Cyber Kill Chain l'APT "Cobalt Group" a-t-il utilisé l'outil
`Sdelete` pour supprimer des données ?

Raisonnement : `Sdelete` est un outil de suppression sécurisée de fichiers. Son usage pour
supprimer des données correspond directement à l'action listée côté attaquant : "Damaging
the system by deleting critical information".

**Réponse : 7 (Actions on Objectives).**

## Point clé

Ce cours boucle la boucle — chaque étape des 7 dépend de la réussite de la précédente. Pour
un analyste, comprendre ce modèle permet de répondre à la question essentielle face à un
incident : "jusqu'où l'attaquant est-il allé, et qu'est-ce que ça implique comme actions de
réponse ?"
