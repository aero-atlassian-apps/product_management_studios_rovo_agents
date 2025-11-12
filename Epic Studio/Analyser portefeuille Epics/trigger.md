## Scénario — Analyser portefeuille Epics

### Déclenchement
Activer quand l’utilisateur veut une vue portefeuille/synthèse sur plusieurs Epics (≥5 conseillé) avec agrégation, tendances, doublons/chevauchements et priorisation.

## Starters de conversation (2 lignes utiles)
- « Panorama des Epics pour `[projet/période]` (≥5) avec recommandations »
- « Analyse portefeuille pour `[liste/JQL]` et proposes 3 actions »
 - « Détecte doublons/chevauchements et propose fusion/re‑scope pour `[liste/JQL]` »
 - « Donne 3 tendances clés et priorités sur `[périmètre]` »

### Exemples positifs
- « Analyse la qualité de ces 20 Epics »
- « Donne un panorama des Epics de ce projet »
- « Rapport portefeuille des Epics du trimestre »
- « Vue portefeuille pour projet [X], période [P], avec priorisation »
- « Donne 3 recommandations (prioriser, re‑scoper, lier) pour ces Epics [liste] »
- « Détecte doublons et propose des fusions »
- « Quels thèmes récurrents et 3 actions ? »

### Exemples négatifs
- « Évalue EPIC‑123 » → Évaluer la qualité d’une Epic
- « Faut‑il fusionner deux Epics ? » → Améliorer une Epic existante

## Frontières et anti‑chevauchement
- Responsabilité unique: vue portefeuille et recommandations sur un ensemble d’Epics.
- Pas d’écriture Jira; produire synthèse et actions.
- Hors portée: travail individuel détaillé sur une seule Epic.

Consolidation
- « Tendances » et « Doublons & chevauchements » sont inclus comme lenses internes.
- L’alignement OKR/Initiatives est traité comme dimension facultative.

## Handoffs (redirections)
- Epic unique à traiter → Améliorer une Epic existante.
 - Intention ambiguë → Accompagner PRODUCT (clarification).