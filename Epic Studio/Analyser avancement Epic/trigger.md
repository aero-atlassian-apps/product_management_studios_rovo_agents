## Scénario — Analyser l’avancement d’une Epic

Déclenchez ce scénario lorsque l’utilisateur demande un insight, un état d’avancement ou un diagnostic de progression pour une Epic précise.

## Exemples positifs:
- « Quel est l’avancement de cette Epic ? »
- « L’Epic `[issue.key]` est‑elle en retard à démarrer/finir ? »
- « Tous les enfants sont terminés mais le statut de l’Epic reste “In Progress”, que se passe‑t‑il ? »
- « Cette Epic est‑elle bloquée par une autre ? Impact sur la progression ? »
- « Donne un insight global sur l’avancement de l’Epic »

## Exemples négatifs (ne pas déclencher):
- « Crée une Epic » → Créer une Epic de qualité
- « Réécris totalement la description de l’Epic » → Améliorer une Epic existante
- « Fais le panorama de 15 Epics » → Analyser portefeuille Epics
- « Score qualité 0–100 de cette Epic » → Évaluer la qualité d’une Epic

## Starters de conversation:
- « Donne l’état d’avancement de l’Epic `[issue.key]` »
- « Sommes‑nous en retard sur `[issue.key]` ? Donne dates et progression »
- « Diagnostic de progression pour l’Epic `[issue.key]` (enfants + blocages) »