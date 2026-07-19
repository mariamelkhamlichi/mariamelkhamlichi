# Command and Control (C2)

## Définition

6e étape du Cyber Kill Chain. L'attaquant a préparé un serveur C2 pour envoyer des commandes
au système compromis. Il peut désormais envoyer des commandes à distance et les exécuter.

## Côté attaquant (Adversary)

Ce que fait l'attaquant ici : établir le contact entre le C2 et le système cible — cette
étape n'inclut pas encore l'exécution des actions finales visées (ça, c'est l'étape
suivante, "Actions on Objectives"). Une fois la communication C2 établie, l'attaquant peut
ensuite passer à l'action.
- Configurer le serveur C2 pour communiquer avec la victime
- Mettre en place les actions nécessaires sur l'appareil de la victime pour rendre ce contact
  possible

## Côté défenseur (Blue Team)

Accent mis sur la surveillance et détection générale du trafic réseau lié au C2 :
- Vérifier si des outils C2 connus sont présents sur les systèmes
- Bloquer les IP de serveurs C2 connues (via Threat Intelligence) au niveau du firewall
- Détecter le trafic pouvant correspondre à une communication C2 via le Network Security
  Monitoring

## Question de la leçon — scénario de détection

> Un analyste observe qu'une machine Windows établit avec succès une connexion vers une IP
> externe suspecte, et en déduit que l'attaquant a pu exécuter des commandes à distance sur
> cette machine.

**Question :** quelle est la dernière étape du Cyber Kill Chain où l'attaquant a réussi ?

Raisonnement : "exécuter des commandes à distance via une connexion établie" = la
communication C2 fonctionne pleinement (l'attaquant contrôle la machine à distance). Rien
n'indique que l'attaquant ait atteint son objectif final (exfiltration, ransomware,
sabotage...) — donc la dernière étape réussie est le Command and Control, étape n°6.

**Réponse : 6 (Command and Control).**

## Point clé

Nuance par rapport à la leçon "Installation" : là, on identifiait où l'attaquant avait
**échoué** ; ici, on identifie la dernière étape où il a **réussi** — deux angles différents
pour le même raisonnement séquentiel du Cyber Kill Chain.
