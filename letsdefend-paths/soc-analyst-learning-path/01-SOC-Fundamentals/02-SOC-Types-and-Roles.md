# SOC Types and Roles

## Définition

Un SOC (Security Operations Center) est une structure où l'équipe sécurité surveille et
analyse en continu la sécurité de l'organisation, dans le but de **détecter, analyser et
répondre** aux incidents de cybersécurité, en combinant technologie, personnes et processus.

## Les 4 modèles de SOC

| Modèle | Description |
|---|---|
| **In-house SOC** | Équipe interne complète, gérée par l'organisation. Nécessite un budget conséquent pour être pérenne. |
| **Virtual SOC** | Pas de site physique dédié, équipe souvent à distance. |
| **Co-Managed SOC** | Équipe interne + MSSP (Managed Security Service Provider) externe. Coordination essentielle. |
| **Command SOC** | Supervise plusieurs SOC plus petits sur une large zone géographique (ex : télécoms, défense). |

## People, Process, Technology

Un SOC efficace repose sur l'équilibre de 3 piliers :

- **People** — personnel formé, capable de s'adapter à l'évolution constante des attaques.
- **Process** — procédures standardisées, alignées sur des référentiels (NIST, PCI-DSS, HIPAA).
- **Technology** — outils de pentest/détection/prévention/analyse. Le meilleur produit du
  marché n'est pas forcément le meilleur pour l'équipe (facteur budget à considérer).

## Rôles dans un SOC

- **SOC Analyst** (Tier 1/2/3) — classe les alertes, identifie la cause, propose la remédiation.
- **Incident Responder** — évalue en premier les violations de sécurité (breach), responsable
  de la détection des menaces.
- **Threat Hunter** — recherche proactivement des menaces cachées (APT) qui échappent aux
  outils classiques.
- **Security Engineer** — maintient l'infrastructure sécurité (SIEM, produits SOC), ex :
  connecte SIEM et SOAR.
- **SOC Manager** — budget, stratégie, gestion d'équipe, coordination (opérationnel, pas technique).

## Point clé

Le SOC Analyst n'est qu'un rôle parmi d'autres dans un écosystème plus large — comprendre les
autres rôles aide à savoir à qui escalader quoi.
