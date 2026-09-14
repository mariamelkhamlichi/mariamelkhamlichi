# SecureKeyBox - Infrastructure Réseau Sécurisée & Authentification Forte

## 🛡️ Contexte du Projet
Ce projet a été réalisé lors d'un stage de perfectionnement au sein de Smart Automation Technologies durant l'été 2026. L'objectif principal est de concevoir et de sécuriser une infrastructure réseau pour protéger l'accès administratif d'un serveur critique[cite: 1]. La solution intègre une authentification forte à deux facteurs (2FA) via un boîtier dédié (SecureKeyBox) et un environnement de supervision SOC complet.

## 🏗️ Architecture et Technologies
L'infrastructure virtualisée repose sur quatre machines isolées par un point de passage obligé (choke point) :
*   **Routeur/Pare-feu/VPN (Master) :** Serveur gérant le routage, le tunnel WireGuard et appliquant une politique Zero Trust où l'accès SSH est strictement restreint à l'interface VPN[cite: 1, 2].
*   **Authentification Forte :** Déploiement d'un service RADIUS relié via PAM pour exiger et valider le second facteur d'authentification[cite: 1, 2].
*   **SIEM et Supervision :** Serveur hébergeant la suite Wazuh (Manager, Indexer, Dashboard) pour la centralisation et l'analyse des événements[cite: 1, 2].
*   **Postes Clients :** Machines Kali Linux simulant l'administration légitime et les attaques offensives (Red Team)[cite: 1, 2].

## ⚙️ Mécanismes de Défense (Blue Team)
*   **Prévention :** Segmentation réseau, filtrage strict par défaut (iptables), et chiffrement intégral des flux avec WireGuard[cite: 1, 2].
*   **Détection :** Règles de corrélation Wazuh personnalisées et enrichies avec le référentiel MITRE ATT&CK (ex: alerte de force brute T1110)[cite: 1, 2].
*   **Réponse Active :** Bannissement automatique des adresses IP malveillantes au niveau du pare-feu grâce à fail2ban[cite: 1, 2].
*   **Leurre :** Intégration du honeypot Cowrie pour piéger les attaquants dans un faux shell et surveiller l'exécution de commandes malveillantes (T1059)[cite: 1, 2].

## 🧠 Détection Comportementale par Machine Learning
Pour pallier les limites des règles statiques, un pipeline d'apprentissage automatique a été développé[cite: 1] :
*   Agrégation des événements de sécurité en fenêtres temporelles de 5 minutes[cite: 1].
*   Déploiement d'un algorithme **Isolation Forest** (non supervisé) détectant les anomalies comportementales avec une exactitude de 0,95[cite: 1, 2].
*   Analyse de l'importance des variables (nombre d'échecs, sévérité maximale) via un modèle Random Forest pour garantir l'explicabilité des alertes[cite: 1, 2].

## 📈 Résultats et Audit
L'infrastructure a bloqué avec succès les scénarios d'attaque Red Team[cite: 1, 2]. Un audit de durcissement mené avec Lynis a permis d'optimiser les paramètres du noyau, renforçant ainsi l'indice de sécurité global du serveur maître[cite: 1, 2].
