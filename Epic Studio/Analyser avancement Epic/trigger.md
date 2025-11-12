## Scénario — Analyser l’avancement d’une Epic

### Déclenchement
Activer lorsque l’utilisateur demande un insight, un état d’avancement ou un diagnostic de progression pour une Epic précise.

## Starters de conversation (2–3 lignes utiles)
- « Donne l’état d’avancement de l’Epic `[issue.key]` »
- « Sommes‑nous en retard sur `[issue.key]` ? Dates et progression »
- « Diagnostic de progression pour l’Epic `[issue.key]` (enfants + blocages) »

### Exemples positifs
- « Quel est l’avancement de cette Epic ? »
- « L’Epic `[issue.key]` est‑elle en retard à démarrer/finir ? »
- « Tous les enfants sont terminés mais le statut de l’Epic est encore “In Progress”, que se passe‑t‑il ? »
- « Cette Epic est‑elle bloquée par une autre ? Impact sur la progression ? »
- « Donne un insight global sur l’avancement de l’Epic »

### Exemples négatifs
- « Crée une Epic » → Créer une Epic de qualité
- « Réécris totalement la description de l’Epic » → Améliorer une Epic existante
- « Fais le panorama de 15 Epics » → Analyser portefeuille Epics
- « Score qualité 0–100 de cette Epic » → Évaluer la qualité d’une Epic

## Frontières et anti‑chevauchement
- Responsabilité: analyser l’avancement d’UNE Epic (dates, statut, progression enfants, liens/dépendances) et produire un insight actionnable.
- Ne pas modifier l’Epic (statut, champs) sans passer par « Améliorer »; par défaut, publication d’un commentaire sur consentement.
- Hors portée: création/réécriture complète, scoring qualité, analyse portefeuille.

## Garde‑fous
- Prérequis: exiger `issue.key` ou URL de l’Epic. Si manquant → poser 1 question ciblée; sinon `PAS_DE_REPONSE_POSSIBLE`.
- Pré‑flight avant consentement: vérifier câblage, permissions, identifiants; si KO/non câblé → fournir un commentaire Markdown prêt à copier‑coller.
- Consentement unique: ne publier le commentaire que sur consentement explicite; confirmer en conversation avec clé/lien après succès.
- Limites: rester sur Epic; ne pas basculer en silence vers un autre scénario; proposer explicitement le handoff si besoin.

## Handoffs (redirections)
- Incohérences statut/contenu → Améliorer une Epic existante (mise à jour structurée).
- Besoin de score/diagnostic qualité → Évaluer la qualité d’une Epic.
- Volume ≥ 5 Epics ou demande portefeuille → Analyser portefeuille Epics.
- Urgence « rapide/express » → Donner un feedback rapide.

Consolidation
- Ce scénario complète le cœur (Créer/Évaluer/Améliorer) par une vue « progression » centrée sur dates/avancement/blocages.