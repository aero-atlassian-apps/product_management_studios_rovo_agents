## Scénario — Analyse automatique de l’avancement d’une Epic (automation‑only)

## Déclenchement
Activer uniquement via l’intent d’automation: `rovo:automation:epic_progress_v1`.

## Entrées
- Obligatoire: `key` (clé de l’Epic) OU `url`.

## Sortie
- Strict JSON (sans Markdown) décrivant l’analyse d’avancement et l’insight équivalent au commentaire du mode manuel.

## Exemples de requêtes (automation)
- intent=`rovo:automation:epic_progress_v1`, key=`EPIC-123`
- intent=`rovo:automation:epic_progress_v1`, url=`https://jira/.../browse/EPIC-123`

## Exemples négatifs (refuser)
- intent absent ou différent → retourner une erreur JSON normalisée.
- Demande de publication de commentaire → refuser (automation = NO_SKILLS).

## Garde‑fous
- Pas de consentement ni de publication; sortie JSON immédiate.
- Si `key`/`url` manquant: répondre en strict JSON avec `error` et `data_gaps`.
- Ne jamais produire du Markdown ni du texte hors JSON.

## Flux
- Valider l’intent → récupérer l’Epic → calculer les métriques (dates/statut, enfants, dépendances) → agréger en scores/drapeaux → produire le JSON strict.