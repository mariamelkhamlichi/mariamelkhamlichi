# Installation

## Définition

5e étape du Cyber Kill Chain. L'attaquant cherche à maintenir un accès persistant sur le
système exploité, généralement via une backdoor. Nécessaire car la vulnérabilité exploitée
finira par être patchée — l'attaquant a besoin d'un autre moyen d'accès qui survivra au
correctif. Le malware peut être déposé via un dropper. Tentative possible d'élévation de
privilèges pour obtenir un compte à hauts droits et assurer la persistance.

## Côté attaquant (Adversary)

L'attaquant essaie de laisser le moins de traces possible et d'éviter les produits de
sécurité, pour rester indétecté plus longtemps. Actions possibles :
- Installer un malware sur l'appareil de la victime
- Placer une backdoor sur le système
- Installer un web shell (si serveur web)
- Ajouter un service, une règle firewall ou une tâche planifiée pour la persistance

## Côté défenseur (Blue Team) — logique du Threat Hunting

Si un attaquant atteint cette étape sans être détecté, il est déjà indétectable par les
moyens classiques. D'où l'approche : opérer en partant du principe qu'un attaquant est
toujours potentiellement présent (posture proactive, pas seulement réactive). Mesures :
- Network Security Monitoring sur tous les assets
- EDR pour surveiller les changements de configuration sur chaque endpoint
- Restreindre et surveiller l'accès aux fichiers/chemins critiques
- N'autoriser les droits admin que quand c'est strictement nécessaire
- Surveiller les processus en cours pour détecter une activité malveillante
- N'autoriser l'exécution que de fichiers signés (signature valide)
- Détecter les anomalies dans l'activité système et en trouver la cause racine

## Question de la leçon — scénario de détection

> Un EDR détecte un malware sur une machine de l'organisation. Après investigation, l'analyste
> détermine que le malware n'a jamais été exécuté et qu'aucune activité système malveillante
> n'a eu lieu.

**Question :** à quelle étape du Cyber Kill Chain l'attaquant a-t-il échoué ?

Raisonnement : le fichier malveillant est bien arrivé sur la machine (**Delivery** réussi),
mais comme il n'a jamais été exécuté, il n'a jamais pu s'activer → l'attaquant a échoué à
l'étape **Exploitation** (étape n°4).

**Réponse : 4 (Exploitation).**

## Point clé

Un fichier malveillant présent mais jamais exécuté = Delivery réussi, Exploitation échouée.
La détection avant exécution est l'un des meilleurs scénarios pour un SOC : l'attaque est
neutralisée avant même d'avoir pu commencer à agir sur le système.
