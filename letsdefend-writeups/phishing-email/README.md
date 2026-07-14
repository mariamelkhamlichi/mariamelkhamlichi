# 🎣 Phishing Email

![Category](https://img.shields.io/badge/Cat%C3%A9gorie-Phishing-orange?style=flat-square) ![Difficulty](https://img.shields.io/badge/Difficult%C3%A9-Easy-brightgreen?style=flat-square) ![Status](https://img.shields.io/badge/Statut-Complété-blue?style=flat-square)

## Contexte
Votre adresse email a fuité, et vous recevez un faux email PayPal (en allemand) — un cas classique de phishing. L'objectif est d'analyser le fichier `.eml` fourni comme le ferait un analyste SOC pour déterminer s'il est malveillant et en extraire les indicateurs de compromission (IOCs).

## Démarche d'investigation

### 1. Analyse des en-têtes email (Return-Path)
Ouverture du `.eml` dans un éditeur de texte pour lire les en-têtes bruts (pas le rendu visuel). Le `Return-Path` indique l'adresse réelle où rebondissent les erreurs d'envoi — souvent différente du `From:` affiché, ce qui trahit une usurpation. Ici : expéditeur affiché `☆P.A.Y.P.A.L☆` mais domaine d'envoi réel `designclub.uk.com` — aucun rapport avec PayPal.

![En-têtes email avec Return-Path suspect](./screenshots/01-email-headers.png)

### 2. Extraction de l'URL malveillante
Dans le corps HTML de l'email, recherche des balises `href=` pour trouver le lien sur lequel la victime est censée cliquer. Trouvé : un lien hébergé sur `storage.googleapis.com` (Google Cloud Storage) — une technique fréquente des attaquants : abuser d'un service cloud légitime pour héberger la fausse page, ce qui aide à contourner les filtres de réputation de domaine.

![Recherche des URLs dans le corps HTML du .eml](./screenshots/02-url-extraction.png)

### 3. Vérification via OSINT (urlscan.io / VirusTotal)
Plutôt que d'ouvrir le lien directement (risqué), utilisation d'outils d'analyse tierce qui font la requête à notre place et en toute sécurité :
- **urlscan.io** : simule une visite du site dans un navigateur sandboxé, montre les requêtes réseau, redirections, et le hash SHA-256 de chaque ressource téléchargée (le "Resource Hash" trouvé).
- **VirusTotal** : agrège les verdicts de dizaines de moteurs antivirus/anti-phishing sur une URL ou un fichier.

![Résultat du scan urlscan.io sur storage.googleapis.com](./screenshots/03-urlscan-result.png)

### 4. Calcul du hash du body
Le SHA-256 du corps de la réponse HTTP sert d'IOC unique et fiable — même si l'URL change, le hash permet d'identifier ce contenu spécifique dans d'autres outils (threat intel, EDR, etc.).

## 🚩 IOCs identifiés
| Type | Valeur |
|---|---|
| Expéditeur usurpé | `☆P.A.Y.P.A.L☆` |
| Domaine d'envoi réel | `designclub.uk.com` |
| URL malveillante | `storage.googleapis.com/...` |
| Hash SHA-256 | body de la ressource (via urlscan.io) |

## ✅ Verdict
Tous les signaux convergent : expéditeur usurpé, domaine d'envoi non lié à PayPal, lien vers une page hébergée abusivement sur un service cloud → **c'est bien un email de phishing.**

## Compétences travaillées
`En-têtes SMTP` `Return-Path/SPF/DKIM/ARC` `Extraction IOCs` `.eml` `OSINT` `urlscan.io` `VirusTotal`

---
*Exercice représentatif du travail quotidien d'un analyste SOC de niveau 1 face à un signalement de phishing par un utilisateur.*
