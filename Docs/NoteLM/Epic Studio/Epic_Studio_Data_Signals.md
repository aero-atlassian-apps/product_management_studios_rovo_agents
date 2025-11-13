# Epic Studio — Signaux de données

## Avancement d’une Epic (signaux)
- Dates: `Created`, `Resolution`, `Start`, `Due`; dérivés: `age_days`, `cycle_time_days`.
- Statut/catégorie: `To Do` / `In Progress` / `Done`; `time_in_status_days`.
- Enfants: total/done/in_progress/todo; % de complétion; orphelins; réouvertures; churn (14 jours).
- Liens: `is blocked by` / `blocks` / `relates to`; champ/étiquette `Flagged`.
- Changelog: dernière transition/activité; transitions sur 14 jours; changement de périmètre.
- Synthèse: `On Track` / `À Risque` / `En Retard` + `confidence`.

## Portefeuille (signaux)
- Distribution de qualité; taux de prêt.
- Doublons/chevauchements; hotspots de priorité.
- Fenêtre temporelle; pagination >10; lot ≤20.