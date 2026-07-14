# Writeups LetsDefend

Analyses réalisées sur la plateforme [LetsDefend](https://letsdefend.io) : investigation d'alertes SOC, réponse à incidents et résolution de challenges, à l'aide de SIEM, EDR et techniques de threat hunting.

## 🧩 Challenges

| Challenge | Catégorie | Résumé |
|---|---|---|
| [Phishing Email](./challenges/phishing-email.md) | Phishing | Analyse d'un fichier `.eml` (faux PayPal) : en-têtes usurpés, extraction d'URL malveillante hébergée sur cloud, vérification OSINT (urlscan.io, VirusTotal) → verdict phishing confirmé |

📁 [Voir le détail des challenges](./challenges)

## 🧪 Labs (Alertes SOC)

*À compléter au fur et à mesure.*

| Lab | Type d'alerte | Verdict |
|---|---|---|
| *(à venir)* | | |

📁 [Voir le détail des labs](./labs)

---

## Structure d'un writeup

Chaque writeup suit ce format :
- **Contexte** : description de l'alerte / du challenge
- **Investigation** : démarche, outils utilisés, requêtes SIEM
- **IOCs identifiés** : IPs, hashs, domaines, etc.
- **Conclusion / Verdict** : True Positive / False Positive, mesures prises
