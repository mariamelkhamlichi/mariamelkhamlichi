# Common Mistakes made by SOC Analysts

Dernière leçon de la section — 4 erreurs classiques à éviter.

## 1. Sur-confiance dans VirusTotal

Un résultat "clean" sur VirusTotal ne garantit pas qu'un fichier/URL est inoffensif : de
nouveaux malwares utilisent des techniques de contournement d'antivirus (AV bypass) non
détectées par VT. VirusTotal doit être traité comme un outil de support, pas une vérité
absolue — mener sa propre analyse en parallèle.

Lecture complémentaire : [VirusTotal is not an Incident Responder](https://medium.com/maverislabs/virustotal-is-not-an-incident-responder-80a6bb687eb9)

## 2. Analyse de malware trop rapide en sandbox

Une analyse de 3-4 minutes peut donner un faux sentiment de sécurité :
- Le malware peut détecter l'environnement sandbox et rester inactif volontairement.
- Certains malwares ne s'activent qu'après 10-15 minutes (délai d'activation intentionnel).

Il faut laisser tourner l'analyse le plus longtemps possible, idéalement en environnement réel.

## 3. Analyse de logs insuffisante

Exemple : un malware détecté sur la machine "LetsDefend" communique avec `letsdefend.io`.
Erreur fréquente : s'arrêter à cette seule machine. Il faut systématiquement utiliser le Log
Management pour vérifier si d'autres machines tentent aussi de contacter cette même adresse
(lien avec la leçon [Log Management](./05-Log-Management.md)).

## 4. Ignorer les dates sur VirusTotal

Une recherche déjà effectuée sur VT renvoie un résultat mis en cache. Piège : un attaquant
peut soumettre une URL propre à VT (résultat clean caché) puis remplacer le contenu par du
malveillant ensuite — le cache reste "clean" alors que le contenu a changé. Toujours vérifier
la colonne "Last Updated" et relancer une nouvelle analyse plutôt que de se fier au cache.

## Point clé

Ces 4 erreurs partagent un thème commun : la confiance excessive dans un seul outil/résultat
sans esprit critique ni vérification croisée. Un bon analyste recoupe toujours plusieurs
sources et prend le temps nécessaire.
