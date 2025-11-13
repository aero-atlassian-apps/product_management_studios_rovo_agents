# Epic Studio — Référence technique

## Architecture

### Routage des scénarios
- Parcours actifs: Créer, Améliorer, Évaluer, Portefeuille, [AUTO] Scoring & évaluation d’une Epic.
- Ordre de sélection (humain):
  1) Créer une Epic de qualité (intention de création)
  2) Améliorer une Epic existante (intention d’optimisation)
  3) Évaluer la qualité d’une Epic (intention de scoring/diagnostic)
  4) Analyser portefeuille Epics (intention multi‑Epics)
- Scénario par défaut: « Accompagner PRODUCT » — utilisé si aucun déclencheur ne correspond; sert au cadrage et au routage.
- [AUTO] Scoring & évaluation d’une Epic: jamais déclenché par l’utilisateur; uniquement par automation (webhook/cron) avec sortie JSON stricte.
- Anti‑chevauchement:
  - Conformité/Ready → traités dans Évaluer/Améliorer; ne pas créer un scénario séparé.
  - Tendances/duplications → lenses dans Portefeuille; pour un seul Epic, utiliser Améliorer.
  - Canevas/modèle → option dans Créer.

### Boucle d’exécution ReAct
- Thought (interne): analyser intention, contraintes, état Jira.
- Action (visible): proposer/agir avec format strict (verbes, données, consentement).
- Observation (visible): rapport concis du résultat ou de l’état.
- Reflection (interne): décider si poursuivre, demander, rediriger, ou s’arrêter.
- Cycles: maximum 3 avant consentement, handoff, ou bloc prêt à copier.

## Patterns d’implémentation

### Registre d’Actions
- `ASK_CLARIFY`: poser une question unique et ciblée pour lever une ambiguïté.
- `ROUTE_SCENARIO`: proposer une redirection vers un scénario plus adapté, avec justification.
- `PREPARE_JIRA_CHANGE`: présenter un diff clair des changements Epic pour consentement.
- `PUBLISH_COMMENT`: publier un commentaire dans Jira après consentement explicite.
- `GENERATE_MARKDOWN`: produire un contenu prêt Jira pour publication manuelle (bloc prêt à copier).
- `VALIDATE_READY`: vérifier la check‑list Ready et signaler les manques.
- `ANALYZE_TRENDS` / `ANALYZE_PORTFOLIO`: analyser et restituer synthèse utile.
- `DETECT_DUPLICATES`: détecter doublons/chevauchements et proposer consolidation.
- `CHECK_COMPLIANCE`: vérifier conformité aux standards et suggérer corrections.
- `ALIGN_OKR`: proposer un alignement stratégique en texte libre (objectifs/initiatives; OKR si disponibles — facultatif).
- `CREATE_EPIC`: créer une Epic selon les champs fournis, avec consentement.
- `ABORT_WITH_FALLBACK`: arrêter proprement — pour un scénario, rediriger vers le parcours par défaut; pour une action, ne pas exécuter et livrer un bloc prêt à copier.
- `STOP`: clore la boucle avec récap et prochaine étape.

### Gestion des signaux
- `PAS_DE_REPONSE_POSSIBLE`: indiquer explicitement l’impossibilité de produire une réponse fiable (infos essentielles manquantes, hors portée, connecteur/permissions indisponibles).
- Usage: en tête de réponse, pour permettre aux automatisations de basculer vers un flux alternatif.
- En cas d’indisponibilité: si une sortie partielle est possible, fournir un Markdown prêt à copier APRÈS la ligne `PAS_DE_REPONSE_POSSIBLE`.
- Ne jamais mixer ce signal avec une confirmation d’action.

## Points d’intégration

### Prérequis connecteurs
- Vérifier que les connecteurs requis (Jira, Docs) sont actifs et que les permissions sont suffisantes pour le projet et le type Epic.
- En cas de connecteur manquant/inactif: ne pas demander de consentement; livrer un bloc prêt à copier + la démarche pour activer (Paramètres Rovo → Connecteurs).
- Normaliser les identifiants d’entrée (`issue.key`/lien Epic, `projectKey`); éviter d’exposer des IDs internes.

### Intents d’automatisation
- `rovo:automation:epic_progress_v1`
  - Entrées: `key` ou `url`; optionnels: `weights`, `stalled_days_threshold`, `locale`.
  - Sortie: JSON strict (métadonnées, scores, risque, insight, recommandations, `changelog_summary`).
- `rovo:automation:epic_score_v1`
  - Entrées: `key` ou `url` + `previous score <VAL|EMPTY>`.
  - Sortie: JSON strict (`key`, `url`, `score`, `insight`, `recommendations`).

## Gestion des erreurs

### Taxonomie des erreurs
- `invalid_intent`: intent d’automatisation absent/invalide.
- `missing_issue_reference`: `key`/`url` manquant.
- `connector_inactive`: connecteur requis indisponible.
- `insufficient_permissions`: droits insuffisants.
- `not_found`: Epic introuvable.

### Stratégies d’indisponibilité (redirection par défaut / bloc prêt à copier)
- Avant action: présenter un diff clair et options.
- Après échec: expliquer simplement, livrer un bloc prêt à copier, proposer la prochaine étape.
- Ne pas divulguer d’erreurs techniques internes; rester centré utilisateur.