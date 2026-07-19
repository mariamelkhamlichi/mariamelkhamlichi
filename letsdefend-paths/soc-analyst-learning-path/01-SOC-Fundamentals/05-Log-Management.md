# Log Management

## Qu'est-ce que le Log Management ?

Solution qui centralise tous les logs d'un environnement (web, OS, firewall, proxy, EDR, etc.)
en un seul endroit, avec recherche unifiée. Évite d'avoir à interroger chaque équipement
séparément (gain de temps, moins d'erreurs).

Sur LetsDefend, la page "Log Management" liste les sources par **Type** (Proxy, Exchange,
Firewall...) avec colonnes : Date, Type, Source Address, Source Port, Destination Address,
Destination Port, Raw.

## Cas d'usage

1. **Recherche de C2 / IOC** — après avoir identifié qu'un malware communique avec un domaine
   C2 (ex: `letsdefend.io`), rechercher ce domaine dans le Log Management pour voir si
   d'autres appareils de l'entreprise ont tenté de le contacter, même sans alerte SIEM associée.
2. **Vérification post-incident** — après isolement d'une machine infectée exfiltrant vers une
   IP suspecte, vérifier si d'autres machines communiquent avec la même IP — le SIEM peut ne
   pas avoir tout détecté.

## Point clé

Le SIEM alerte sur des événements déjà jugés suspects par ses règles ; le Log Management
permet une recherche manuelle et exhaustive sur l'historique brut, utile pour compléter ce
que le SIEM a pu manquer.

## Exercice pratique (Log Search)

- Recherche de l'IP source ayant accédé à une URL donnée (ex: via colonne Raw / Source Address).
- Identification du type de log à partir d'un port de destination + IP source
  (ex: port 53 / trafic vers 8.8.8.8 → type `dns`).

### Exemple : recherche via "New Search" (page Log Management, LetsDefend)

Champ de recherche : `Raw Log contains "https://github.com/apache/flink/compare"` (plage
"All Time"). Résultat : 1 événement trouvé, avec le détail des champs ("Interesting Fields") :

| Field | Value |
|---|---|
| type | Proxy |
| source_address | 172.16.17.54 |
| source_port | 54211 |
| destination_address | 140.82.121.3 |
| destination_port | 443 |
| time | Dec 19, 2020, 09:15 AM |
| Raw Log → Request URL | https://github.com/apache/flink/compare |

**À retenir :** la recherche `Raw Log contains "<texte>"` permet de retrouver un événement à
partir d'une chaîne présente dans le log brut (ici une URL complète), même sans connaître à
l'avance le type de log ou l'adresse IP concernée — utile quand on part d'un indicateur
(IOC) trouvé ailleurs (ex: dans un rapport de malware) et qu'on veut savoir qui y a été exposé.

### Exemple 2 : recherche via "Source Address contains"

Champ de recherche : `Source Address contains "8.8.8.8"` (plage "All Time"). Résultat :
1 événement trouvé :

| Field | Value |
|---|---|
| type | **DNS** |
| source_address | 8.8.8.8 |
| source_port | 53 |
| destination_address | 172.16.17.81 |
| destination_port | 52567 |
| time | Aug 11, 2022, 07:57 AM |
| Raw Log → Standard Response A | 3.134.39.220 |

**À retenir :** le port source **53** et l'IP source **8.8.8.8** (résolveur DNS public Google)
sont deux indices forts qu'il s'agit de trafic **DNS** — même logique que reconnaître le
port 25 pour SMTP ou 443 pour HTTPS : les numéros de port standards aident à identifier le
type de log/protocole sans même lire le champ `type`.
