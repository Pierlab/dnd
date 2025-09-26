# Instructions générales du dépôt

## Principes fondamentaux
- Ce dépôt suit la **méthode de vibe coding de Mozi**. Avant toute modification, relire `docs/methode_vibe_coding_mozi.md`, l'étoile polaire et le backlog pour rester aligné.
- Documenter chaque contribution dans `docs/backlog.md` en respectant l'ordre chronologique (dernière entrée en bas).
- Les commits doivent refléter des itérations courtes et cohérentes.
- Utiliser le français pour les documents et commentaires.
- Les nouvelles ressources doivent préserver la vision stratégique du set/campagne décrite dans l'étoile polaire.

## Logique de conduite d'une partie
1. Lire intégralement `player_input.md` pour assimiler l'état courant de la scène et les questions du joueur.
2. Consulter l'historique pertinent (`docs/histoire_session_en_cours.md`, journaux, fiches) si nécessaire afin de garantir la cohérence narrative.
3. Préparer la réponse au joueur :
   - Résoudre les actions demandées en décrivant les conséquences de manière immersive.
   - Proposer la suite de la scène en restant fidèle à l'étoile polaire et aux informations canoniques.
   - Mettre à jour `player_input.md` avec un résumé clair de la nouvelle situation et les invites destinées au joueur.
4. Actualiser l'état du monde et les journaux concernés avec toute information nouvelle (PNJ, indices, ressources, etc.).
5. Vérifier avant validation que chaque action de jeu a été consignée et que les documents impactés sont synchronisés.

## Jets de dés et aléatoire
- Les résolutions aléatoires doivent refléter de vrais jets de dés (d4, d6, d8, d10, d12, d20, etc.).
- Utiliser la console de l'agent pour générer les résultats :
  ```bash
  python - <<'PY'
  import random
  print(random.randint(1, 20))  # exemple de jet de d20
  PY
  ```
- Adapter la borne supérieure au type de dé requis (ex. `random.randint(1, 6)` pour un d6) et annoncer dans la narration le résultat du jet ainsi que le dé utilisé.
- Conserver une trace des jets effectués dans les journaux ou fiches concernés afin de garantir la transparence vis-à-vis du joueur.
