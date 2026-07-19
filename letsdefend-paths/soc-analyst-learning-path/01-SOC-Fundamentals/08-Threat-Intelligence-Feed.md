# Threat Intelligence Feed

## Définition

Un Threat Intelligence Feed est une base de données fournie par un tiers, contenant des
artefacts d'activités malveillantes passées : hashs de malware, IP/domaines de C2, etc.
Utilisé pour vérifier si un indicateur (hash, IP...) a déjà été associé à une menace connue.

## Sur LetsDefend (Threat Intel page)

Table avec colonnes : Date, Data Type (Hash/IP), Data (valeur), Tag (malware / phishing /
spam), Score, Data Source (ex : Abuse.ch, ou "Anonymous").

## Sources gratuites populaires

- [VirusTotal](https://www.virustotal.com/)
- [Talos Intelligence](https://talosintelligence.com/)

## Deux pièges importants

1. **Absence de résultat ≠ fichier propre.** Si un hash ne remonte rien dans les feeds, ça
   ne signifie pas que le fichier est sain (peut-être trop récent ou jamais soumis ailleurs).
   Il faut quand même effectuer une analyse statique/dynamique du fichier — ne jamais
   conclure uniquement sur l'absence de match.

2. **Une IP peut changer de propriétaire dans le temps.** Exemple : un attaquant loue un
   serveur AWS comme C2 → l'IP est listée malveillante dans les feeds → quelques mois plus
   tard, le serveur est fermé et quelqu'un d'autre récupère cette IP pour un usage légitime
   (ex : blog perso). Une IP malveillante par le passé ne l'est pas forcément aujourd'hui —
   toujours vérifier la fraîcheur/date de l'info threat intel, pas seulement sa présence.

## Point clé

Le Threat Intelligence Feed est un outil d'aide à la décision, pas une vérité absolue, dans
les deux sens (absence ≠ innocent, présence passée ≠ malveillant aujourd'hui). Le jugement
de l'analyste reste indispensable.
