# SOAR (Security Orchestration Automation and Response)

## Définition

Le SOAR fait travailler ensemble les différents outils de sécurité d'un environnement, en
automatisant des tâches répétitives. Exemple : recherche automatique de la réputation d'une
IP source d'alerte SIEM sur VirusTotal, sans intervention manuelle de l'analyste.

Solutions SOAR courantes : Splunk Phantom, IBM Resilient, Logsign, Demisto.

## Les 3 apports principaux

1. **Gain de temps** — automatise des workflows répétitifs : réputation IP, recherche de
   hash, scan d'un fichier en sandbox, etc.
2. **Centralisation** — une seule plateforme regroupant les différents outils (sandbox, log
   management, outils tiers...) au lieu de jongler entre plusieurs interfaces.
3. **Playbooks** — procédures pré-écrites par scénario d'incident :
   - Permet d'investiguer sans connaître par cœur toutes les étapes.
   - Standardise le travail de toute l'équipe (garantit que les étapes obligatoires, ex :
     vérifier la réputation IP, sont bien suivies par tous les analystes).

## SOAR sur LetsDefend = "Case Management"

- Liste des cas (**Open** / **Closed**), chacun lié à un EventID/règle SIEM (ex :
  `SOC157 - Suspicious WAR File`, `SOC145 - Ransomware Detected`, `SOC101 - Phishing Mail
  Detected`, `SOC160 - ZBot Application Detected`, `SOC155 - Hijacked NPM Package`,
  `SOC152 - Encrypted Files Detected`, `SOC156 - Unnormal Code/Command Execution`).
- Ouvrir un cas → un **playbook est automatiquement assigné**, avec des questions guidées.
  Exemple : *"What is the initial access method used in the attack?"*, avec des choix basés
  sur **MITRE ATT&CK - Initial Access** (Phishing, Exploit Public-Facing Application, Valid
  Accounts, Supply Chain Compromise, External Remote Services, None).

## Point clé

Le SOAR n'est pas un outil de plus à côté du SIEM/EDR/Log Management : il les **orchestre**
et automatise les tâches répétitives, tout en garantissant via les playbooks une
investigation cohérente et complète par toute l'équipe. Premier lien avec **MITRE ATT&CK**,
approfondi dans la section 3 du path.
