## Scénario — Pré‑valider avant Ready

### Déclenchement
Activer quand l’utilisateur veut vérifier l’état « Ready/Prêt » d’une Epic selon une liste de contrôle minimale (DoR).

## Starters de conversation (2 lignes utiles)
- « Pré‑valider Ready (DoR) pour l’Epic `[issue.key]` »
- « Lister 3 blocants qui empêchent `[issue.key]` d’être Ready »

### Exemples positifs
- « Mon Epic est‑elle prête pour le statut Prêt ? »
- « Fais la pré‑vérification avant la transition »
- « Qu’est‑ce qui bloque la validation de cette Epic ? »
- « Mon Epic est‑elle Ready (DoR) ? »
- « Pré‑valide Ready pour [clé] et liste 3 blocants »
- « Donne 3 actions pour passer en Ready »

### Exemples négatifs
- « Donne un score à l’Epic » → Évaluer la qualité d’une Epic
- « Réécris/Améliore cette Epic » → Améliorer une Epic existante
- « Vérifie la conformité au guide » → Vérifier conformité standards

## Frontières et anti‑chevauchement
- Responsabilité unique: pré‑validation DoR avant passage à Ready.
- Ne change pas le statut; produit une liste de blocants et actions.
- Hors portée: reformulation complète ou scoring.

## Handoffs (redirections)
- Conformité au guide → Vérifier conformité standards.
- Actions d’amélioration → Améliorer une Epic existante.
- Décomposition backlog → [Ouvrir Product Backlog Studio](https://home.atlassian.com/o/c4dj6dbj-dbk7-1kk9-ja37-j1j98277a9d2/chat?rovoChatPathway=chat&rovoChatCloudId=2dddf9c5-88e5-400a-a21a-739ce4738f14&rovoChatAgentId=f1b04611-623e-4ef4-aba0-a80ba8a29a94&cloudId=2dddf9c5-88e5-400a-a21a-739ce4738f14).