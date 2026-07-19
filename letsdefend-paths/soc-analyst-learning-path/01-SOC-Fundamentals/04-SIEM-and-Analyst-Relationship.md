# SIEM and Analyst Relationship

## Qu'est-ce qu'un SIEM ?

SIEM = Security Information and Event Management. Solution qui journalise les événements
en temps réel dans l'environnement, dans le but de détecter les menaces de sécurité.
Fonctionnalités clés pour un analyste : collecte + filtrage des données, génération d'alertes
sur événements suspects.

**Exemple** : 20 mots de passe erronés en 10s sur un compte Windows → comportement suspect →
une règle SIEM (seuil/filtre) détecte ce dépassement et génère une alerte.

Solutions SIEM connues : IBM QRadar, ArcSight ESM, FortiSIEM, Splunk.

## Relation Analyste ↔ SIEM

L'analyste SOC se concentre principalement sur le suivi des alertes (d'autres équipes gèrent
la configuration des règles/corrélations). Flux : données → filtres → alerte → l'analyste
détermine si c'est une vraie menace ou un faux positif, avec l'aide d'autres outils (EDR,
Log Management, Threat Intelligence Feed).

## Workflow des alertes (LetsDefend / SOC typique)

- **Main Channel** — canal partagé, nouvelles alertes visibles par toute l'équipe.
- **Take Ownership** — action qui déplace l'alerte vers l'**Investigation Channel** ;
  signale à l'équipe que l'alerte est prise en charge (évite les doublons de travail).
- Détails de l'alerte disponibles au clic : hostname, IP, hash de fichier, etc.
- **Closed Alerts** — alertes traitées/clôturées.

## Quick Tip — faux positifs

Un bon analyste identifie les alertes mal calibrées et remonte le feedback à l'équipe SIEM
pour optimiser les règles.

**Exemple** : règle alertant sur toute URL contenant "union" (détection SQLi type
`UNION SELECT`). Une recherche Google `sql union usage` déclenche l'alerte sans menace réelle
→ faux positif dû à un mot-clé trop générique, à signaler pour affiner la règle.

## Point clé

Le SIEM filtre/alerte ; c'est l'analyste qui juge du vrai/faux et documente sa prise en charge
via le workflow Main → Investigation → Closed.
