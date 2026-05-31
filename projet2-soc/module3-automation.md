# Module 3 : Automatisation du Flux de Réponse aux Incidents avec n8n

Ce fichier documente la conception du flux automatisé permettant de corréler la détection d'un journal d'audit (log) suspect avec l'ouverture automatique d'un ticket de remédiation cyber.

## 📐 Architecture du Flux (Workflow n8n)

1. **Webhook (Déclencheur) :** Réception en temps réel des alertes de connexion inhabituelles poussées par le SIEM ou un script de collecte.
2. **AI Processing Node :** Transmission du log brut à notre agent IA (Module 2). L'IA qualifie le comportement selon le Playbook interne.
3. **Data Parsing :** Extraction des blocs `STATUT`, `ANALYSE` et `PROCÉDURE INTERNE` générés par l'IA.
4. **Router / Switch :** * Si `STATUT` == `SUSPECT` ➡️ Branche Incident (Création de ticket).
   * Si `STATUT` == `CONFORME` ➡️ Branche Archivage (Clôture silencieuse).
5. **Action Incident (TheHive / Jira) :** Création automatique d'un ticket de sécurité contenant l'analyse contextuelle de l'IA et la procédure exacte à appliquer par l'équipe d'astreinte.

## 🧪 Test de Validation du Pipeline

### Log d'Audit en Entrée :
```text
2026-05-31 03:12:45 UTC - Successful login for user a.martin from IP 198.51.100.42 port 52110 ssh2 - Note: User usually connects from Europe/Paris (IP 82.x) between 08:00 and 18:00. Current connection from Asia/Seoul at 03:12 AM.

Analyse et Remédiation extraites par l'IA :
Plaintext

STATUT : SUSPECT
ANALYSE : La connexion est réussie, mais elle présente une anomalie géographique et temporelle majeure par rapport au profil habituel de l'utilisateur. a.martin se connecte habituellement depuis la France (fuseau Europe/Paris) durant les heures de bureau (08h00 - 18h00), alors que cette session provient d'une IP localisée en Corée du Sud (Asia/Seoul) à 03h12 du matin. Cela correspond au Cas C du playbook interne (Activité suspecte hors profil).
PROCÉDURE INTERNE :
- Activer une surveillance accrue sur le compte.
- Contacter l'utilisateur pour confirmation de l'activité.
