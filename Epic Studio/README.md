# Epic Studio — Guide et standardisation

Ce répertoire regroupe des scénarios d’assistance autour des Epics Jira (création, amélioration, analyse, conformité, etc.). Il fournit des instructions et des déclencheurs normalisés pour garantir des réponses cohérentes et des garde‑fous opérationnels.

## Structure du répertoire
- `Scénario/`
  - `instructions.md` — guide d’exécution et de qualité (sections standardisées)
  - `trigger.md` — conditions de déclenchement et starters de conversation
  - `skills.md` — capacités autorisées (lecture/commentaire; actions limitées selon garde‑fous)
- `Docs/Templates/` — modèles d’instructions et de triggers pour créer de nouveaux scénarios

## Principes clés
 - Portée Epic uniquement: agir et commenter sur les Epics; rediriger stories/tâches/bugs vers [Ouvrir Product Backlog Studio](https://home.atlassian.com/o/c4dj6dbj-dbk7-1kk9-ja37-j1j98277a9d2/chat?rovoChatPathway=chat&rovoChatCloudId=2dddf9c5-88e5-400a-a21a-739ce4738f14&rovoChatAgentId=f1b04611-623e-4ef4-aba0-a80ba8a29a94&cloudId=2dddf9c5-88e5-400a-a21a-739ce4738f14).
- Pré‑validation avant toute demande de consentement: connecter, vérifier permissions et identifiants.
- Consentement unique: ne jamais redemander pour la même action dans la même session; afficher résumé/diff.
- Sortie lisible et actionnable: puces prioritaires, ≤180 mots par défaut, format Jira prêt à copier.

## Créer un nouveau scénario
1. Dupliquer les deux templates dans `Docs/Templates/`:
   - `instructions_template.md` → adapter les sections ci‑dessous.
   - `triggers_template.md` → compléter « Quand déclencher », starters et exemples.
2. Renseigner `skills.md` avec les capacités autorisées (souvent `COMMENT_WORK_ITEM`).
3. Vérifier les garde‑fous: portée, pré‑validation, consentement unique, redirections explicites.
4. Ajouter 2 starters de conversation utiles dans `trigger.md`.
5. Tester localement la cohérence des sections et la clarté des exemples.

## Sections standardisées — `instructions.md`
- Audience typique
- Longueur cible
- Format de réponse / Style
- Objectif, Contexte et hypothèses
- Déclencheur (prompt de démarrage)
- Entrées requises
- Processus détaillé
- Sorties attendues
- Garde‑fous et limites (incluant portée Epic, pré‑validation, consentement)
- Snippets de consentement et post‑consentement
- Exemples de prompts (starter)
- Follow‑ups recommandés

## Sections standardisées — `trigger.md`
- Quand déclencher ce scénario
- Starters de conversation (2 lignes utiles)
- Exemples positifs (doivent déclencher)
- Exemples négatifs (ne doivent pas déclencher)
- Exemples org‑spécifiques
- Frontières et anti‑chevauchement
- Garde‑fous et Handoffs
- Formats acceptés et Mots‑clés utiles

## Checklist de cohérence
- Le scénario reste strictement dans la portée Epic; redirections claires si hors‑portée.
- Les starters sont spécifiques, actionnables, et orientés résultat/mesure.
- La pré‑validation décrit précisément les identifiants requis et le fallback.
- Les sorties sont compactes, prêtes à copier, et priorisées par impact.
- Les `skills.md` respectent les garde‑fous (souvent commentaire‑only) et l’absence de YAML/IDs exposés.

## Maintenance
- Aligner tout nouveau scénario sur les templates mis à jour.
- Réviser périodiquement les garde‑fous et les redirections adjacentes.
- Tenir à jour les starters de conversation pour refléter la pratique réelle.