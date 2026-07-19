# Weaponization

## Définition

2e étape du Cyber Kill Chain. L'attaquant utilise les infos collectées en Reconnaissance pour
accéder aux outils nécessaires à l'attaque, ou les développer lui-même (exploit, malware,
contenu de phishing...). Si les outils sont déjà prêts, cette étape peut être rapide.

**Point important :** l'attaque n'a pas encore commencé — la victime n'a généralement aucune
idée qu'elle est ciblée à ce stade.

## Côté attaquant (Adversary)

- Création de malware
- Développement d'exploits
- Création de contenu malveillant pour du phishing (template email, document piégé)
- Identification du meilleur outil pour l'attaque prévue

## Côté défenseur (Blue Team)

Impossible d'empêcher directement la préparation de l'attaquant (hors de portée de
l'organisation), mais on peut limiter les risques en amont :
- Vérifier régulièrement l'existence de vulnérabilités connues sur les systèmes
- Installer les mises à jour de sécurité rapidement
- Suivre les nouveaux outils d'attaque connus/émergents pour détecter leur usage plus tard

## Question de la leçon — scénario d'attaque (organisation télécom)

> 1. APT cible une organisation télécom
> 2. Adresses email collectées via réseaux sociaux/sources ouvertes
> 3. Template d'email de phishing généré
> 4. Document Word "Salaries.docx" avec macro malveillante créé
> 5. Email de phishing envoyé aux employés
> 6. Email consulté, document téléchargé par certains employés
> 7. Document ouvert, macro exécutée
> 8. Ransomware installé et exécuté via PowerShell

Analyse phrase par phrase :
1. Ciblage de l'organisation → **Reconnaissance**
2. Collecte d'adresses email → **Reconnaissance**
3. Création du template de phishing → **Weaponization**
4. Création du document piégé → **Weaponization**
5. Envoi de l'email → **Delivery**
6. Email consulté / document téléchargé → **Delivery**
7. Document ouvert / macro exécutée → **Exploitation**
8. Ransomware installé et exécuté → **Installation**

**Réponse : 2 actions distinctes de Weaponization** (création du template + création du
document piégé — les deux "fabrications" d'armes, avant tout envoi/interaction avec la
victime).

## Point clé

Weaponization = fabrication de l'arme (contenu/outil malveillant). Dès qu'il y a envoi ou
interaction avec la victime, on bascule dans l'étape suivante (Delivery).
