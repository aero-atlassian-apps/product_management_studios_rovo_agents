# Epic Studio — Guide des scénarios

## Scénario par défaut (routage)
- Déclenchement: demande floue; aucune correspondance avec un autre scénario.
- Entrées: texte libre.
- Sortie: compréhension + prochaine étape + exemple de commande.
- Rôle: router vers un scénario Epic supporté (incl. portefeuille).

## Créer une Epic de qualité
- Déclenchement: créer/rédiger une Epic.
- Entrées: objectifs, utilisateurs, impacts, critères; `projectKey`.
- Sortie: Epic en Markdown validée; proposer création (consentement).

## Évaluer la qualité d’une Epic
- Déclenchement: évaluer/noter/diagnostiquer une Epic existante.
- Entrées: `issue.key` ou URL; mode score ou avis rapide.
- Sortie: score global/par dimension + recommandations.

## Améliorer une Epic existante
- Déclenchement: optimiser/réviser/corriger une Epic.
- Entrées: `issue.key` ou URL; sections à améliorer si connues.
- Sortie: rapport + version révisée (Markdown/diff); édition sur consentement.

## Analyser avancement Epic (manuel)
- Déclenchement: besoin d’un diagnostic d’avancement.
- Entrées: `issue.key` ou URL; dates, enfants, liens, changelog.
- Sortie: insight court + actions; commentaire prêt à publier.

## [AUTO] Analyser avancement Epic
- Déclenchement: intent `rovo:automation:epic_progress_v1`.
- Entrées: `key`/`url`; `weights`, `stalled_days_threshold`, `locale`.
- Sortie: JSON strict (métadonnées, scores, risque, changelog).

## [AUTO] Scoring & évaluation d’une Epic
- Déclenchement: intent `rovo:automation:epic_score_v1`.
- Entrées: `key`/`url`; `previous score <VAL|EMPTY>`.
- Sortie: JSON strict (`score`, `insight`, `recommendations`).

## Analyser portefeuille Epics
- Déclenchement: vue synthèse multi‑Epics (≥5 conseillé).
- Entrées: liste de clés/liens ou périmètre/JQL.
- Sortie: synthèse qualité en lot + priorisation; alimente Améliorer.