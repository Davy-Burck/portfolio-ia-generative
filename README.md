
# Portfolio IA Générative & Agents — Spécialisation Cybersécurité

Bienvenue sur mon journal de bord et portfolio dédié à l'apprentissage de l'IA Générative et à son intégration dans les processus de Cybersécurité. Ce dépôt regroupe mes travaux pratiques, mes architectures d'agents et mes configurations.

##  Sommaire
* [Statut de progression des Projets](#statut-de-progression-des-projets)
  * [Projet 1 : Le Veilleur Cyber Automatique](#projet-1--le-veilleur-cyber-automatique)
  * [Projet 2 : L'Analyseur de Logs Suspects (SOC Assistant)](#projet-2--lanalyseur-de-logs-suspects-soc-assistant)
  * [Projet 3 : Le Vulgarisateur & Générateur de Fiches de Sensibilisation](#projet-3--le-vulgarisateur--générateur-de-fiches-de-sensibilisation)
* [Technologies utilisées](#technologies-utilisées)
* [Gouvernance & Sécurité IA](#gouvernance--sécurité-ia)

---

## Statut de progression des Projets

### Projet 1 : Le Veilleur Cyber Automatique
Automatisation d'une veille sur les menaces et vulnérabilités (Flux RSS/API) avec tri intelligent par LLM et alertes.
- [ ] Module 1 : Conception du Prompt Système & de la logique de filtrage
- [ ] Module 2 : Enrichissement du contexte (RAG basique sur criticité CVE)
- [ ] Module 3 : Automatisation du workflow complet sur n8n
- [ ] Module 4 : Sécurisation du pipeline contre l'injection de données

### Projet 2 : L'Analyseur de Logs Suspects (SOC Assistant)
Analyse contextuelle de logs système pour détecter des comportements anormaux ou malveillants.
- [ ] Module 1 : Création du prompt Few-Shot de classification de logs
- [ ] Module 2 : Connexion à la documentation de référence (MITRE ATT&CK) via RAG
- [ ] Module 3 : Intégration dans un flux d'analyse d'incident
- [ ] Module 4 : Audit de sécurité des données (éviter les fuites de logs sensibles dans le LLM)

### Projet 3 : Le Vulgarisateur & Générateur de Fiches de Sensibilisation
Transformation de rapports techniques complexes en notes de sécurité claires et fiches de sensibilisation pour les collaborateurs.
- [ ] Module 1 : Création de l'assistant custom (Gem/Project) avec ton managérial
- [ ] Module 2 : Fiabilisation des faits via des techniques de réduction d'hallucinations
- [ ] Module 3 : Déploiement d'une interface ou d'un canal de génération à la demande
- [ ] Module 4 : Conformité RGPD et politiques de rétention des données

---

## Technologies utilisées
- **LLMs :** Gemini (Advanced), Claude 3.5
- **Frameworks & Concepts :** Prompt Engineering, RAG (Retrieval-Augmented Generation), Few-Shot Learning, AI Guardrails
- **Automatisation :** n8n

---

## Gouvernance & Sécurité IA
> 🛡️ **Sécurité & Gouvernance IA :** Consulte le détail de l'approche risque, des garde-fous et de la validation par projet dans [GOUVERNANCE_SECURITE_IA.md](./GOUVERNANCE_SECURITE_IA.md).
