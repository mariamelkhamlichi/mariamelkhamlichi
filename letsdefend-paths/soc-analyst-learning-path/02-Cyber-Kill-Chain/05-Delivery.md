# Delivery

## Définition

3e étape du Cyber Kill Chain. L'attaquant exécute réellement l'attaque préparée : première
interaction avec la victime. Ex : le malware est mis en ligne, la victime le télécharge.
Méthodes variables selon le type d'attaque (email, site web, réseaux sociaux, support
physique...).

## Côté attaquant (Adversary)

- URL malveillante envoyée par email
- Malware en pièce jointe email
- Malware distribué via un site web
- URL malveillante via réseaux sociaux
- Malware via réseaux sociaux
- Upload direct du malware sur le serveur cible (si accès direct possible)
- Installation physique via clé USB

## Côté défenseur (Blue Team)

- Se méfier systématiquement des URLs dans les emails, les analyser en sandbox
- Scanner les pièces jointes avec un antivirus
- Utiliser des solutions de sécurité email
- Former les employés à la sécurité de l'information
- Surveiller en continu les accès serveur, conserver les logs
- Gérer efficacement les firewalls
- Analyser en détail toute activité suspecte
- Détecter les anomalies et en identifier la cause racine

## Question de la leçon — scénario d'attaque (secteur défense, USB drop)

> 1. APT cible une institution du secteur défense
> 2. IP détectées via Shodan et Zoomeye
> 3. OS Windows identifié via sources ouvertes
> 4. Malware intégré dans "putty.exe" via Metasploit
> 5. Malware transféré sur plusieurs clés USB
> 6. Clés USB déposées sur le trottoir près de l'institution
> 7. Un employé branche une clé USB sur un poste du réseau de l'entreprise
> 8. Il exécute "putty.exe" depuis la clé USB
> 9. L'attaquant obtient une exécution de commandes à distance via connexion inversée
> 10. L'attaquant ajoute une tâche planifiée pour la persistance
> 11. L'EDR marque la tâche planifiée comme suspecte
> 12. Le SOC analyst remarque l'alerte "Suspicious Scheduled Task Detected"
> 13. Après analyse, l'analyste empêche l'attaque d'aller plus loin

Analyse phrase par phrase :
1. Ciblage → **Reconnaissance**
2. Détection IP (Shodan/Zoomeye) → **Reconnaissance**
3. OS identifié → **Reconnaissance**
4. Malware intégré dans putty.exe → **Weaponization**
5. Malware transféré sur clés USB → **Weaponization** (encore en préparation, pas encore
   dans l'environnement de la cible)
6. Clés USB déposées près de l'institution → **Delivery** (le vecteur atteint la proximité
   de la cible)
7. Employé branche la clé USB → **Delivery** (transmission effective dans l'environnement cible)
8. Exécution de putty.exe → **Exploitation**
9. Connexion inversée / commandes à distance → **Installation / C2**
10. Tâche planifiée (persistance) → **Installation**
11-13. Détection EDR, alerte SOC, action de l'analyste → actions du défenseur, hors kill
   chain attaquant

**Réponse Weaponization : 2 actions** (intégration du malware dans putty.exe + transfert sur
les clés USB).

**Réponse Delivery : 2 actions** (dépôt des clés USB à proximité + branchement par l'employé).

## Point clé

La frontière Weaponization/Delivery se situe au moment où l'arme quitte l'espace de
préparation de l'attaquant et entre dans l'environnement/portée de la victime. Tant que le
support (ex : clé USB) est "chez l'attaquant", c'est Weaponization ; dès qu'il est
physiquement accessible à la cible, c'est Delivery.
