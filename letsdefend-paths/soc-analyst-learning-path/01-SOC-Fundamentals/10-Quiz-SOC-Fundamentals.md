# Quiz de validation — SOC Fundamentals

Quiz final de la section (13 questions), avec réponses et justification basées sur les
leçons 1 à 9.

**Q1. Which type of SOC team does not have its own facility and often works remotely in
different locations?**
Réponse : **Virtual SOC**
→ Pas de site fixe, travail à distance ([leçon 2](./02-SOC-Types-and-Roles.md)).

**Q2. I am responsible for connecting security products. My job title is ...**
Réponse : **Security engineer**
→ C'est lui qui connecte les produits de sécurité (ex : SIEM ↔ SOAR).

**Q3. What is SOC?**
Réponse : **Security Operation Center**

**Q4. Which tool is the most important for a SOC analyst?**
Réponse : **All of this, and much more**
→ Aucun outil seul ne suffit : SIEM + EDR + Log Management + threat intel se complètent.

**Q5. Which type of SOC model corresponds to: "consists of internal SOC personnel working
with an external Managed Security Service Provider"?**
Réponse : **Co-Managed SOC**

**Q6. Which SOC position corresponds to: "A team member whose purpose is to find
vulnerabilities before the attacker can exploit them in an attack"?**
Réponse : **Threat Hunter**
→ Recherche proactive des menaces avant qu'elles ne fassent des dégâts.

**Q7. What is the goal of a SIEM?**
Réponse : **To provides the real time logging of events in an environment.**
→ Définition SIEM de la [leçon 4](./04-SIEM-and-Analyst-Relationship.md).

**Q8. Which LetsDefend's page is the SIEM?**
Réponse : **Monitoring**

**Q9. What is an EDR?**
Réponse : **A software that monitor the terminals (computers, servers, tablets, phones...)
and not the information system network.**
→ L'EDR surveille les endpoints, pas le réseau global (rôle du Log Management/SIEM).

**Q10. What are the different steps of the lifecycle for the NIST, of an incident?**
Réponse : **Preparation, Detection/Analysis, Containment/Eradication and Recovery,
Post-Event Activity**
→ Cycle de vie NIST SP 800-61. (Les autres options : Cyber Kill Chain, gestion de risque
générique, cycle non-standard.)

**Q11. What can be used to conduct an analysis with SOAR?**
Réponse : **Playbook**
→ Outil central du SOAR pour guider l'investigation ([leçon 7](./07-SOAR.md)).

**Q12. Which information do you not have in the Threat Intelligence Feed?**
Réponse : **A sample of the infected file**
→ Le TI Feed donne hash/IP/score/source, jamais le fichier lui-même
([leçon 8](./08-Threat-Intelligence-Feed.md)).

**Q13. Which is a common mistake for SOC analysts?**
Réponse : **Insufficient log analysis**
→ L'une des 4 erreurs explicitement listées dans la
[leçon 9](./09-Common-Mistakes-made-by-SOC-Analysts.md).

## Score

13/13 revues et justifiées.
