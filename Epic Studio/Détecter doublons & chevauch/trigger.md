## Scénario — Détecter doublons & chevauch

### Déclenchement
Activer quand l’utilisateur doit identifier doublons/chevauchements entre Epics (contenu, objectifs, périmètre).

## Starters de conversation (2 lignes utiles)
- « Détecter chevauchements entre `[EPIC‑A]` et `[EPIC‑B]` »
- « Lister doublons pour ces Epics: `[liste]` »

### Exemples positifs
- « Est‑ce que ces deux Epics sont en doublon ? »
- « Détecte les chevauchements dans ces Epics »
- « Dois‑je fusionner ces Epics ? »
- « Détecte les doublons sur ces 12 Epics » (> 10 → Portefeuille)
- « Détecte doublons pour [clé] dans le projet [X] et propose une action »
- « Repère chevauchements avec ces Epics [liste] et suggère fusion/re‑scope »

### Exemples négatifs
- « Détecte les doublons sur tout le projet » → Analyser portefeuille Epics
- « Faut‑il fusionner/scinder ? » → Améliorer une Epic existante
- « Valide le statut Ready » → Pré‑valider avant Ready

## Frontières et anti‑chevauchement
- Responsabilité unique: détecter doublons/chevauchements et proposer des options.
- Pas d’édition ni création; commentaires possibles sur consentement.
- Hors portée: arbitrage final de fusion/scission.

## Handoffs (redirections)
- Arbitrage et actions de fusion/scission → Améliorer une Epic existante.
- Ambiguïté ou besoin de décision → Accompagner PRODUCT.
 - Décomposition en stories → [Ouvrir Product Backlog Studio](https://home.atlassian.com/o/c4dj6dbj-dbk7-1kk9-ja37-j1j98277a9d2/chat?rovoChatPathway=chat&rovoChatCloudId=2dddf9c5-88e5-400a-a21a-739ce4738f14&rovoChatAgentId=f1b04611-623e-4ef4-aba0-a80ba8a29a94&cloudId=2dddf9c5-88e5-400a-a21a-739ce4738f14).