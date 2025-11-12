# Scoring automatique d’une Epic — Trigger (Automation‑only)

Intent unique (obligatoire)
- Utiliser exactement: `rovo:automation:epic_score_v1`
- Doit apparaître en tête du message d’automatisation.

Conditions d’entrée
- Le message inclut soit une `key` (ex: `EPIC-123`) soit une `url` (ex: `https://.../browse/EPIC-123`).
- Le prompt DOIT inclure `previous score <VAL>` où `<VAL>` est une valeur numérique (ex: `78`, `78.4`, `0.85`, `85%`) ou le mot clé `EMPTY` si aucun score précédent n’est disponible.
- Lorsque les deux (`key` et `url`) sont disponibles dans le contexte d’automatisation, les utiliser.

Garde‑fous (anti‑chat)
- Si l’intent `rovo:automation:epic_score_v1` est absent ou si l’item n’est pas fourni, refuser poliment: « Ce scénario est réservé à l’automatisation Jira. Utilise “Évaluer la qualité d’une Epic” en chat. »
- Ne pas demander de consentement: ce scénario est non interactif et doit produire une sortie immédiatement.

Sortie attendue (strict JSON, aucune prose)
- Un objet JSON unique, sans backticks, sans Markdown.
- Clés: `key`, `url`, `score`, `insight`, `recommendations`.

Exemple d’appel (Jira Automation)
```
rovo:automation:epic_score_v1 EPIC-123 previous score {{issue.customfield_10091}}

<coller ici le contenu synthétique de l’Epic, son champ description, objectifs, critères, etc.>

-- ou --

rovo:automation:epic_score_v1 https://jira.example.com/browse/EPIC-123 previous score EMPTY

<coller ici le contenu synthétique de l’Epic, son champ description, objectifs, critères, etc.>
```

Exemple de sortie (documentation, ne pas inclure de texte autour)
```
{
  "key": "EPIC-123",
  "url": "https://jira.example.com/browse/EPIC-123",
  "score": 85,
  "insight": "Première évaluation: critères partiellement conformes; objectifs insuffisamment mesurables.",
  "recommendations": [
    "Préciser résultats mesurables et indicateurs",
    "Ajouter critères d’acceptation GIVEN/WHEN/THEN",
    "Relier à objectifs/initiatives (OKR si disponibles)"
  ]
}
```