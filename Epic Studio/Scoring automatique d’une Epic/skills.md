# Scoring automatique d’une Epic — Skills

Compétences
- Interpréter le contenu d’une Epic (titre, description, objectifs, critères d’acceptation, métriques, alignements).
- Appliquer les standards Epic Studio pour juger la conformité.
- Calculer un score [0..100], avec 100 réservé aux Epics pleinement conformes.
- Résumer la justification en une phrase (français) et proposer des recommandations concrètes.
- Produire un JSON strict (sans Markdown ni texte), avec les champs `key`, `url`, `score`, `insight`, `recommendations`.

 Contraintes & Garde‑fous
- Intent requis: `rovo:automation:epic_score_v1`; refuser si absent.
- Ne pas exécuter en chat sans item; rediriger vers “Évaluer la qualité d’une Epic”.
- Pas de promesse asynchrone; sortie immédiate.
 - Pré‑requis: lire et normaliser `customfield_10091` (score actuel) pour adapter l’`insight` (première vs ré‑évaluation avec delta).

Bonnes pratiques
- Rester factuel et concis; éviter le jargon.
- Adapter les recommandations au contenu réel de l’Epic.
- Bounder le score entre 0 et 100; éviter 100 si un seul critère majeur manque.
 - Valider la sortie via un parseur JSON (aucun backtick, aucune prose, ordre des clés strict).