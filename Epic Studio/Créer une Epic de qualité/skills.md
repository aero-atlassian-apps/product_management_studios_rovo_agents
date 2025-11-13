CREATE_WORK_ITEM
EDIT_WORK_ITEM
COMMENT_WORK_ITEM
Skills
CREATE_WORK_ITEM
COMMENT_WORK_ITEM

Quand utiliser
- CREATE_WORK_ITEM: créer l’Epic après pré‑flight et consentement explicite.
- COMMENT_WORK_ITEM: publier le brouillon/validation en commentaire (sur consentement).

Prérequis
- `projectKey`, type=Epic, Résumé, Description conformes au canevas.
- Connecteur câblé et permissions suffisantes.

Limitations
- Ne pas décomposer en stories/sous‑tâches (hors portée de ce scénario).
- Ne pas évaluer/scorer ici.

Bonnes pratiques
- Produire un Markdown prêt à créer; convertir en ADF si requis par le connecteur.
- Demander une seule fois le consentement (après pré‑flight) et confirmer en conversation (clé/lien).