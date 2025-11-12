## Scénario — Accompagner PRODUCT

### Déclenchement
Activer quand l’intention est ambigüe ou mixte autour des Epics et que l’utilisateur demande « comment procéder » ou « quoi faire ensuite ».

## Starters de conversation (2 lignes utiles)
- « Aide à cadrer mon intention autour de l’Epic `[issue.key]` »
- « Propose 3 options et prochaines étapes pour `[idée/objectif]` »

### Exemples positifs
- « J’ai une Epic, tu peux m’aider ? »
- « Faut‑il l’améliorer ou juste l’évaluer ? »
- « Que proposes‑tu pour mon Epic ? »
- « Je ne sais pas par où commencer »
- « Sparring sur l’idée [X] avec métrique cible [Y] »
- « Donne 3 options avec trade‑offs et prochaines étapes »

### Exemples négatifs
- « Explique comment utiliser l’agent » → Expliquer comment utiliser
- « Donne un score à EPIC‑123 » → Évaluer la qualité d’une Epic
- « Crée une nouvelle Epic pour X » → Créer une Epic de qualité
- « Détecte doublons sur tout le projet » → Analyser portefeuille Epics

## Frontières et anti‑chevauchement
- Responsabilité unique: clarifier l’intention, cadrer, et proposer options/étapes.
- N’exécute pas d’actions Jira; sert au routage éclairé.
- Hors portée: exécutions directes sans clarification.

## Handoffs (redirections)
- Après clarification → rediriger explicitement vers Créer/Améliorer/Évaluer/etc. avec consentement.
- Items de backlog (stories/tâches) → [Ouvrir Product Backlog Studio](https://home.atlassian.com/o/c4dj6dbj-dbk7-1kk9-ja37-j1j98277a9d2/chat?rovoChatPathway=chat&rovoChatCloudId=2dddf9c5-88e5-400a-a21a-739ce4738f14&rovoChatAgentId=f1b04611-623e-4ef4-aba0-a80ba8a29a94&cloudId=2dddf9c5-88e5-400a-a21a-739ce4738f14).
- Portée multi‑Epics → Analyser portefeuille Epics.