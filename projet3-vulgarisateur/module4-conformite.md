# Module 4 : Conformité RGPD et Application du Principe de Minimisation des Données

Ce fichier documente les garde-fous de confidentialité intégrés au pipeline de sensibilisation pour garantir qu'aucune donnée personnelle superflue ou sensible ne soit traitée ou exposée lors de la génération automatisée des messages.

## 🛡️ Règle de Conformité et Respect de la Vie Privée (RGPD)
Afin de respecter le principe de minimisation (Art. 5 du RGPD), l'instruction suivante a été ajoutée pour restreindre le traitement de l'IA aux seules variables nécessaires :

```text
[CONFORMITÉ RGPD & MINIMISATION]
- Tu dois appliquer de manière stricte le principe de minimisation des données. Les seules données personnelles autorisées dans ta génération sont le prénom, le nom et le poste de l'employé.
- Si le contexte d'entrée contient des informations personnelles non nécessaires (téléphone, adresse, données financières), tu dois les ignorer totalement et ne jamais les faire figurer dans ton message.

Test de Validation (Simulation d'Entrée Non Conforme)
Flux RH Entrant avec Fuite de Données Privées (Entrée) :
Plaintext

Nom : Sarah Moreau
Poste : Développeuse
Téléphone personnel : +33 6 12 34 56 78
Adresse : 45 Rue de la Paix, Paris
Statut financier : RIB validé pour le salaire

Message Épuré et Conforme Généré par l'IA (Sortie) :
Plaintext

Bonjour Sarah Moreau, et bienvenue dans l'équipe en tant que Développeuse !
En tant que formateur en cybersécurité, je suis ravi de t'accueillir. Pour protéger au mieux nos outils et ton nouvel environnement de travail, voici un petit rappel simple des règles essentielles à suivre concernant la gestion de tes mots de passe :
- La longueur : Ton mot de passe doit comporter au moins 12 caractères.
- La complexité : Il doit être composé de 4 types de caractères différents (des majuscules, des minuscules, des chiffres et des caractères spéciaux).
- L'unicité (la règle d'or) : Tu dois utiliser un mot de passe unique pour chaque compte professionnel. Il ne faut jamais réutiliser un mot de passe personnel dans le cadre de ton travail.
- Le stockage : Il est strictement interdit d'écrire tes mots de passe sur des post-it ou dans un fichier texte non sécurisé. Pour les conserver, l'utilisation d'un gestionnaire de mots de passe validé par l'entreprise est obligatoire.

Bonne installation dans tes nouvelles fonctions ! Si tu as des questions sur ces bonnes pratiques
