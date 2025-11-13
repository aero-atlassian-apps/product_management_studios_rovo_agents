# Epic Studio — Mini Cheat Sheet (NoteLM)

## Scénarios et starters
- Scénario par défaut (routage)
  - Clarifier la demande et recommander le meilleur scénario
  - Proposer la prochaine étape avec un exemple de commande
- Créer une Epic de qualité
  - Créer une nouvelle Epic pour un sujet dans un projet
  - Rédiger une Epic orientée résultat pour un objectif
  - Démarrer depuis le modèle standard pour un sujet
- Évaluer la qualité d’une Epic
  - Évaluer une Epic et donner un score synthétique
  - Score par dimension (contexte/objectif/critères)
  - Avis rapide non‑noté pour une Epic (diagnostic express)
- Améliorer une Epic existante
  - Améliorer une Epic existante (clarifier, structurer, reformuler)
  - Proposer 3 corrections prioritaires pour une Epic
  - Vérifier conformité et Ready d’une Epic
- Analyser avancement Epic (manuel)
  - Donner l’état d’avancement d’une Epic
  - Sommes‑nous en retard sur une Epic ? Donner dates et progression
  - Diagnostic de progression (enfants + blocages)
- [AUTO] Analyser avancement Epic (automation‑only)
  - Diagnostic automatique d’avancement (JSON strict)
- [AUTO] Scoring & évaluation d’une Epic (automation‑only)
  - Scoring automatique + recommandations (JSON strict)
- Analyser portefeuille Epics
  - Panorama d’Epics (≥5) avec recommandations
  - Détecter doublons/chevauchements et proposer fusion/re‑scope
  - Donner 3 tendances clés et priorités sur un périmètre

## Commandes rapides (exemples)
- Évaluer qualité d’une Epic
  - « Évaluer la qualité d’une Epic et donner un score »
- Améliorer une Epic
  - « Proposer 3 corrections prioritaires pour une Epic »
- Avancement (manuel)
  - « Donner l’état d’avancement d’une Epic (dates, progression, blocages) »
- Portefeuille
  - « Panorama des Epics pour un périmètre (≥5) et 3 actions prioritaires »

## Automation — intents (exemples)
```text
intent=rovo:automation:epic_progress_v1
key=EPIC-123
locale=fr-FR
weights.s=0.4; weights.e=0.4; weights.d=0.2
stalled_days_threshold=7
```
```text
intent=rovo:automation:epic_score_v1
url=https://jira.example/browse/EPIC-123
previous score=EMPTY
locale=fr-FR
```

## Handoffs typiques
- Avancement → Améliorer (si blocages/qualité faible)
- Évaluer (score < seuil) → Améliorer
- Portefeuille → Améliorer (lot priorisé)
- Hors portée Epic → Ouvrir Product Backlog Studio (décomposition stories)

## Bonnes pratiques
- Pré‑flight avant consentement; publication uniquement sur consentement explicite
- Réponses synthétiques en français; sorties prêtes à copier (Markdown)
- Automation: produire un JSON strict, sans texte ni Markdown