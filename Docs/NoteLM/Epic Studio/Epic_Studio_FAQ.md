# Epic Studio — FAQ

## À quoi sert Epic Studio ?
- Orchestrer le cycle de vie des Epics: créer, évaluer, améliorer, analyser avancement et portefeuille.

## Quelles sont ses limites ?
- Portée Epic uniquement; pas de Stories/Tasks/Subtasks. Redirection explicite si hors périmètre.

## Comment l’automatisation fonctionne‑t‑elle ?
- Via intents (`rovo:automation:epic_progress_v1`, `rovo:automation:epic_score_v1`) avec sorties JSON strictes.

## Publie‑t‑il automatiquement dans Jira ?
- Non. Publication uniquement sur consentement explicite et pré‑flight réussi.

## Que faire si une action n’est pas câblée ?
- Recevoir un bloc prêt à copier avec la démarche manuelle; prochaines étapes indiquées.

## Quels sont les prérequis ?
- Connecteurs actifs et permissions; références minimales (`issue.key`/URL, `projectKey`).

## Comment sont gérées les erreurs ?
- Taxonomie claire; explications simples; bloc prêt à copier; aucune erreur technique exposée.

## Comment éviter les chevauchements de scénarios ?
- Handoffs explicites et anti‑chevauchement (Portefeuille pour multi‑Epics; Améliorer pour une Epic).