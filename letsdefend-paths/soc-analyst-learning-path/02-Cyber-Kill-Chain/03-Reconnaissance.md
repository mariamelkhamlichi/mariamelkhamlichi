# Reconnaissance

## Définition

Première étape du Cyber Kill Chain. L'attaquant cherche à collecter un maximum d'informations
sur sa cible. Plus il en sait, plus la surface d'attaque apparente s'élargit, révélant des
vecteurs d'attaque potentiels.

## Deux sous-catégories

- **Passive Reconnaissance** — collecte sans interaction directe avec le système cible
  (ex : archives web/Wayback Machine pour des infos qui ne sont plus visibles aujourd'hui).
- **Active Reconnaissance** — collecte via interaction directe avec la cible (ex : requête
  à un serveur web pour lire sa version dans la réponse).

## Côté attaquant (Adversary)

- Récupérer les versions de serveurs/logiciels de la cible
- Exploiter des sources ouvertes (OSINT) ayant déjà fuité des infos
- Collecter des adresses email des employés
- Récupérer des infos personnelles via les réseaux sociaux
- Détecter les appareils connectés à Internet
- Détecter des vulnérabilités sur les serveurs exposés
- Identifier le bloc d'IP de l'organisation
- Identifier les prestataires/fournisseurs de l'organisation

## Côté défenseur (Blue Team)

- Pentest externe pour détecter les zones de fuite d'information
- Threat Intelligence pour repérer des fuites déjà connues
- Ne pas laisser de documents internes accessibles publiquement
- Surveiller le trafic (firewalls) sur les zones exposées à Internet
- Patcher rapidement pour éviter l'exploitation de nouvelles vulnérabilités

## Questions de la leçon

**Q1.** Étape où se fait la collecte d'information → **Reconnaissance**

**Q2. Scénario réel (APT38 / Lazarus Group, détection 2019)**

> - APT38 cible une institution financière
> - Information collectée via reconnaissance sur le site web pendant plusieurs jours
> - Vulnérabilité CVE-2019-0604 trouvée dans Microsoft SharePoint
> - Vulnérabilité exploitée
> - Backdoor "Powershell Empire" déployé après l'exploit

Analyse phrase par phrase :
1. Ciblage/sélection de l'organisation → **Reconnaissance** (le ciblage est le point de
   départ de la collecte d'informations, ça compte comme une action à part entière)
2. Collecte d'info via recon sur le site web → **Reconnaissance**
3. Découverte de la vulnérabilité CVE-2019-0604 → **Reconnaissance** (détection de
   vulnérabilité = action listée côté Adversary)
4. Exploitation de la vulnérabilité → étape **Exploitation**
5. Déploiement du backdoor → étape **Installation**

**Réponse correcte : 3 actions distinctes de Reconnaissance** (confirmé par la plateforme).

## Point clé

Toute détection de vulnérabilité ou collecte d'info en amont (même via une CVE connue) fait
partie de la Reconnaissance — l'Exploitation ne commence qu'au moment où la vulnérabilité est
réellement utilisée pour obtenir un accès.
