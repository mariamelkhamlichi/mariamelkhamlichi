# SOC Analyst and Their Responsibilities

## Définition du rôle

Le SOC Analyst est la première personne à investiguer une menace sur un système. Si la
situation l'exige, il escalade l'incident à ses superviseurs pour la mitigation. C'est le
premier point de contact face à une menace au sein de l'équipe SOC.

## Avantages du métier

- Les techniques d'attaque et malwares évoluent constamment → le travail reste varié
  (mêmes OS/outils, mais incidents différents à chaque fois).
- Pas d'exposition systématique à toutes les techniques (variation dans le temps).

## Une journée type

Revue continue des alertes SIEM pour déterminer lesquelles sont de réelles menaces, à l'aide
d'outils comme EDR, Log Management et SOAR (détaillés plus loin dans le cours).

## Compétences clés pour ne pas dépendre uniquement des outils

1. **Operating Systems (Windows/Linux)** — connaître le comportement normal d'un système
   pour repérer l'anormal (ex : services Windows légitimes vs suspects).
2. **Network** — savoir identifier des connexions vers des IP/URLs malveillantes, comprendre
   les bases réseau pour détecter une éventuelle fuite de données.
3. **Malware Analysis** — identifier le vrai objectif d'un malware (qui peut changer de
   comportement pour tromper l'analyste), déterminer a minima son C2 (Command & Control) et
   si une machine y communique.

## Point clé

Un bon SOC Analyst ne dépend pas uniquement des produits de sécurité : les compétences
OS / réseau / malware analysis sont ce qui permet une analyse correcte et autonome des
alertes SIEM.
