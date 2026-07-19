# EDR - Endpoint Detection and Response

## Définition

L'EDR (Endpoint Detection and Response) est une solution de sécurité intégrée qui combine
surveillance continue en temps réel des données d'un endpoint (poste/serveur) avec des
capacités de réponse automatisée basée sur des règles et d'analyse. Utilisé pour investiguer
au niveau de la machine, en complément du SIEM (alerte) et du Log Management (logs réseau
centralisés).

Solutions EDR courantes : CarbonBlack, SentinelOne, FireEye HX.

## Fonctionnalités (page "Endpoint Security", LetsDefend)

- Liste des endpoints accessibles, recherche par nom/IP, ou recherche d'un **IOC**
  (hash de fichier, IP, nom de process...) sur tous les hosts simultanément.
- Pour un device donné : infos générales (OS, bit level, domaine, utilisateur principal,
  dernière connexion) + accès à :
  - Browser History
  - Command History
  - Network Connections
  - Process List (ex : `AcroRd32.exe`, `Chrome.exe`, `mshta.exe`, `cmd.exe`, `taskkill.exe`)

## Live Investigation

Bouton **Connect** → accès direct à la machine pour continuer l'investigation en live
(exploration du bureau, fichiers présents, etc.).

## Containment (isolation réseau)

Isole une machine compromise du réseau interne **et** externe pour :
1. Empêcher l'attaquant de garder une connexion vers l'extérieur.
2. Empêcher un mouvement latéral vers d'autres machines internes.

Le toggle "Request Containment" isole la machine, qui ne peut plus communiquer qu'avec le
serveur central de l'EDR — l'analyse peut continuer malgré l'isolement ("Host Contained").

## Quick Tip — recherche par IOC

Avec un indicateur (ex : hash MD5 d'un fichier malveillant), rechercher dans l'EDR sur
l'ensemble des hosts permet d'identifier toutes les machines touchées par une même attaque,
pas seulement celle initialement détectée.

## Point clé

L'EDR est aussi essentiel que le Log Management pour un analyste. Beaucoup d'analystes le
sous-exploitent — bien maîtriser la recherche IOC cross-host et le containment est un vrai
avantage.

## Exercice pratique (Endpoint Security)

- Recherche d'un hash de fichier (`nmap`, `83e0cfc95de1153d405e839e53d408f5`) → identifier le
  hostname où il s'exécute (`EricProd`, `172.16.17.22`). Confirmé via la barre de recherche
  globale d'Endpoint Security : coller le hash retourne directement les hosts correspondants.
- Depuis le Command History d'un host (`Roberto`, `172.16.17.38`, Windows 10), retrouver la
  commande complète ayant exécuté un fichier suspect (`Ps1.hta`) :
  `C:/Windows/System32/mshta.exe C:/Users/roberto/Desktop/Ps1.hta`
  → `mshta.exe` est souvent utilisé pour exécuter du code malveillant (HTA) en contournant
  certaines protections, à surveiller comme technique d'attaque.
- La commande suivante dans l'historique (10:30, une minute après) lance PowerShell avec une
  fonction encodée (`powershell.exe function H1($i) {$r = "..."}`) — enchaînement typique
  mshta → PowerShell utilisé pour exécuter du code obfusqué en mémoire (technique
  "living off the land").

### Vue détaillée d'un host (onglets)

La fiche d'un endpoint (ex : Roberto) est organisée en 4 onglets :
- **Processes** — liste des processus en cours/historiques
- **Network Action** — connexions réseau initiées par la machine
- **Terminal History** — commandes exécutées (CMD/PowerShell), avec horodatage
- **Browser History** — navigation web

Le toggle **Containment** est disponible directement dans la fiche du host (colonne Action),
pas seulement depuis la vue liste.
