# Chroniques des Royaumes Brisés

Ce dépôt suit la méthode de vibe coding de Mozi pour piloter une campagne de jeu de rôle persistante.

## Directives récentes
- L'agent doit lire `player_input.md`, répondre explicitement aux questions posées par le joueur et préparer le prompt suivant en conséquence.
- Après chaque réponse, l'agent met à jour l'état de la partie ainsi que `player_input.md`.
- `player_input.md` fait désormais office de terminal d'interaction : il est réécrit à chaque itération pour résumer la scène en cours et demander explicitement au joueur quelles actions entreprendre. La réponse du joueur devient le prompt de l'itération suivante.
- Un journal narratif incrémental est consigné dans `docs/histoire_session_en_cours.md` afin que le joueur puisse relire l'évolution de la partie.

Consulter `docs/requirements.md` pour la description complète du projet et `docs/backlog.md` pour l'historique des contributions.
