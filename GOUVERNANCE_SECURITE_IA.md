---

##  Gouvernance, Sécurité & Méthodologie de Validation IA

L'intégration des LLM dans des processus de cybersécurité (veille, SOC, reporting) introduit des risques spécifiques (hallucinations, injections indirectes, fuite de données sensibles). Chaque projet de ce portfolio applique une démarche inspirée des standards d'audit et de test de sécurité (PTES / OWASP LLM Top 10) :

### 1. Principes de contrôle appliqués aux projets
* **Contrôle des hallucinations & reproductibilité :** Aucune sortie générée par un LLM (score CVE, qualification d'alerte MITRE ATT&CK, synthèse de rapport) n'est considérée comme une vérité absolue. Les réponses sont ancrées via **RAG** sur des sources fiables et soumises à une validation humaine avant action.
* **Confidentialité & conformité RGPD :** Les données injectées dans les prompts (notamment les journaux système du *Projet 2* et les rapports internes du *Projet 3*) sont filtrées et anonymisées en amont afin d'éviter toute exposition d'identifiants, d'adresses IP internes ou de données personnelles à des API tierces.
* **Périmètre & autonomie maîtrisée :** Les workflows automatisés (*n8n*) fonctionnent avec des garde-fous stricts (validation des entrées/sorties, cloisonnement des permissions) sans exécution autonome d'actions critiques sur une infrastructure sans approbation humaine.

### 2. Synthèse des risques et mesures de sécurité par projet

| Projet | Risque principal identifié | Mesure de protection & validation | Statut |
| :--- | :--- | :--- | :--- |
| **Projet 1 : Veilleur Cyber** | **Prompt Injection indirecte** via des flux RSS ou descriptions de vulnérabilités malveillantes. | Séparation stricte entre instructions système et données externes, filtrage des entrées et vérification manuelle des alertes critiques. | En cours |
| **Projet 2 : Analyseur de Logs** | **Fuite de données sensibles** (PII, tokens, secrets) vers le LLM et **faux positifs/négatifs** sur l'analyse SOC. | Anonymisation préalable des logs, ancrage sur le référentiel **MITRE ATT&CK** via RAG et relecture systématique par un analyste. | En cours |
| **Projet 3 : Vulgarisateur** | **Hallucinations techniques** déformant un constat d'audit ou non-respect des durées de rétention RGPD. | Contraintes de citation des sources, baisse de la température du modèle, relecture humaine et politique de non-rétention des documents sensibles. | En cours |
