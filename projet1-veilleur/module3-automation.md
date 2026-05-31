# Module 3 : Automatisation du Workflow de Veille avec n8n

Ce fichier documente la conception du flux d'automatisation (Workflow) permettant de connecter un flux de Threat Intelligence entrant à notre agent IA, puis de filtrer les alertes critiques.

## 📐 Architecture du Flux (Workflow n8n)

1. **Trigger (Déclencheur) :** Nœud RSS/Atom configuré sur les flux d'alertes de l'ANSSI (vérification toutes les heures).
2. **Data Transformation :** Extraction du titre et du corps de l'article de veille.
3. **AI Node (Gemini API) :** Envoi du texte brut à notre agent structuré (Module 2). L'IA renvoie le JSON standardisé.
4. **Conditional Switch (IF) :** * Si `statut` == `CRITIQUE` ➡️ Branche A (Alerte Immédiate).
   * Si `statut` == `ÉLEVÉ` ou `MOYEN` ➡️ Branche B (Stockage).
5. **Actions Finales :**
   * **Branche A :** Envoi d'un webhook vers un canal Discord de l'équipe Cyber (SecOps).
   * **Branche B :** Insertion automatique dans une base de données Notion / Airtable pour archivage.

## ⚙️ Configuration du Nœud de Condition (Code d'aiguillage)
Pour lire le JSON généré par l'IA au module précédent, le nœud de condition utilise cette logique :

```javascript
// Extraction de la criticité depuis le nœud Gemini
return items[0].json.statut === "CRITIQUE";

Scénario de Test Global

    Entrée simulée : Publication d'une faille 0-day touchant Windows Server (Exécution de code à distance sans authentification).

    Comportement attendu du pipeline : Le flux RSS s'active ➡️ Gemini analyse et répond statut: "CRITIQUE" ➡️ Le nœud IF valide la condition ➡️ L'alerte pop sur le Discord de l'équipe en moins de 5 secondes.
