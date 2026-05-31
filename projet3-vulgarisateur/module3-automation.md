# Module 3 : Automatisation du Flux de Sensibilisation des Collaborateurs avec n8n

Ce fichier documente la conception du flux automatisé permettant de déclencher un message de sensibilisation personnalisé à la cybersécurité dès l'intégration d'un nouvel employé dans le système RH.

## 📐 Architecture du Flux (Workflow n8n)

1. **Trigger (Déclencheur RH) :** Détection d'un nouvel enregistrement dans l'outil RH (ex: Notion, HiBob ou Airtable) indiquant l'arrivée d'un collaborateur.
2. **Data Extraction :** Récupération du prénom, du nom et de l'intitulé du poste (ex: Lucas Silva, Comptable).
3. **AI Generation Node :** Envoi de ces variables à notre agent IA (Module 2). L'IA génère un message d'accueil personnalisé incluant les directives de sécurité obligatoires de l'ANSSI.
4. **Delivery Node (Notification) :** Envoi automatisé du contenu généré via l'API de communication interne (Slack, Microsoft Teams ou e-mail de bienvenue).

## 🧪 Test de Validation du Pipeline

### Données RH entrantes (Payload) :
```text
Nom : Lucas Silva
Poste : Comptable

Message de sensibilisation généré automatiquement :
Plaintext

Bonjour Lucas, et bienvenue dans l'équipe !
En tant que comptable, vous allez manipuler des données importantes, et la sécurité de notre entreprise commence par de bonnes habitudes numériques. Pour vous accompagner au mieux, voici un bref rappel de la règle d'or de l'entreprise concernant le choix de vos mots de passe :
Unicité absolue : Vous devez utiliser un mot de passe unique pour chaque compte professionnel. De plus, il ne faut jamais réutiliser un mot de passe personnel au travail.

Pour aller plus loin : comment créer un mot de passe conforme ?
- Longueur minimale : Votre mot de passe doit comporter au moins 12 caractères.
- Complexité : Il doit obligatoirement contenir 4 types de caractères (des majuscules, des minuscules, des chiffres et des caractères spéciaux).
- Stockage sécurisé : Il est strictement interdit d'écrire vos mots de passe sur des post-it ou dans un fichier texte non sécurisé. Vous devez obligatoirement utiliser le gestionnaire de mots de passe validé par l'entreprise.

Je vous souhaite une excellente intégration parmi nous ! Si vous avez la moindre question sur ces
