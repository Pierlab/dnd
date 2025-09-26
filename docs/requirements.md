# Projet "Chroniques des Royaumes Brisés"

## 1. Vision générale
- **Type de projet** : campagne de jeu de rôle Donjons & Dragons (D&D 5e inspiré) pilotée via un dépôt Git.
- **Objectif** : offrir une expérience narrative persistante où chaque session influence durablement l'état du monde.
- **Mode d'interaction** : le joueur consigne ses décisions et actions dans un fichier Markdown partagé (`player_input.md`). L'agent lit ce fichier à chaque itération pour adapter la narration, effectuer les jets de dés et mettre à jour les données. À partir du 2025-09-29, `player_input.md` est réécrit par l'agent à chaque tour pour résumer la situation et demander explicitement au joueur quelles suites il choisit. La réponse du joueur sert de prompt direct pour l'itération suivante.

## 2. Contexte narratif
### 2.1 Cadre historique
- **Nom du monde** : Elyndor.
- **Événement fondateur** : la fracture de l'Obélisque d'Auralis il y a trente ans, libérant des flux de magie sauvage et provoquant une famine arcanique.
- **Conséquence** : éclatement de l'Empire central (Auralis) en quatre royaumes rivaux en guerre.

### 2.2 Royaumes en guerre
1. **Valoria** (ancien cœur impérial)
   - Gouvernement : conseil de maisons nobles.
   - Forces : armée disciplinée, maîtrise des artefacts impériaux.
   - Faiblesses : divisions internes, manque de ressources.
2. **Thorgar** (nord montagneux)
   - Gouvernement : confédération clanique.
   - Forces : guerriers runiques, forges naines.
   - Faiblesses : isolement, tensions entre clans.
3. **Serelune** (archipel maritime)
   - Gouvernement : matriarcat mystique.
   - Forces : flotte, mages de marée, réseau d'espions.
   - Faiblesses : instabilité magique accrue par la fracture.
4. **Khar'Seth** (désert méridional)
   - Gouvernement : théocratie du Soleil Voilé.
   - Forces : prêtres-guerriers, armée de djinns liés.
   - Faiblesses : dépendance au cristal solaire, rébellions.

### 2.3 Enjeux persistants
- **Guerre totale** : conquête du trône impérial vacant.
- **Menace externe** : l'Ombre d'Ashkar, entité née de la fracture, grandit à chaque conflit non résolu.
- **Flux de magie** : zones instables qui peuvent muter le terrain ou les habitants.

### 2.4 Ton et thèmes
- Épopée sombre, intrigues politiques, diplomatie fragile.
- Choix moraux avec répercussions à long terme.
- Exploration de ruines impériales et de frontières sauvages.

## 3. Structure de campagne
### 3.1 Arcs narratifs
1. **Arc I – Braises d'Empire** : introduction, prise de conscience de la fracture politique.
2. **Arc II – Ombres Croissantes** : découverte de l'Ombre d'Ashkar et des flux magiques.
3. **Arc III – Tempêtes de Sang** : escalade des guerres, alliances forcées.
4. **Arc IV – L'Héritier de l'Obélisque** : résolution finale, reconstitution ou destruction de l'Empire.

Chaque arc est composé de plusieurs **chapitres**. Chaque partie de jeu doit :
- Établir un **enjeu initial**.
- Introduire un **complication majeure**.
- Se conclure sur un **cliffhanger** ou une conséquence durable.
- Mettre à jour l'état global du monde.

### 3.2 Progression des enjeux
- Les parties démarrent avec des conflits locaux et progressent vers des décisions affectant des nations entières.
- Les conséquences accumulées modifient la difficulté des défis, l'accès à des ressources et l'attitude des factions.

### 3.3 Gestion des saisons
- Regrouper plusieurs sessions en **saisons** (printemps, été, automne, hiver).
- Chaque saison applique des modificateurs : disponibilité des ressources, météo, types de rencontres.

## 4. Persistance et stockage de données
### 4.1 Structure du dépôt
```
/README.md                  — aperçu du projet
/docs/histoire_session_en_cours.md — journal narratif incrémental de la session
/docs/requirements.md       — ce document
/data/world_state.json      — état global du monde (royaumes, cartes, événements)
/data/sessions/<date>.json  — journal des sessions
/data/characters/<id>.json  — fiches des personnages joueurs et PNJ importants
/player_input.md            — fichier d'interaction joueur
/logs/dice_rolls.log        — trace des jets de dés effectués par l'agent
```

### 4.2 Contenu des fichiers
- **world_state.json** :
  - `timeline`: événements datés (arc, saison, session, description, impact).
  - `factions`: état diplomatique, ressources, leaders.
  - `regions`: climat, contrôle, menaces, anomalies magiques.
  - `global_effects`: influences persistantes (bénédictions, malédictions, guerre).
- **sessions/*.json** : résumé détaillé, décisions du joueur, jets importants, conséquences.
- **characters/*.json** :
  - Métadonnées (nom, classe, niveau, historique, alignement).
  - **Caractéristiques** : FOR, DEX, CON, INT, SAG, CHA.
  - **Domaines** : Dialogue, Magie, Combat, Déplacement, Crochetage, Artisanat, Connaissances, Survie, Influence.
  - Capacités de classe et équipement.
  - Relations avec les factions et réputation.
- **player_input.md** :
  - Format structuré (voir section 8).
  - Historique des choix et intentions pour la prochaine session.
- **logs/dice_rolls.log** :
  - `timestamp`, `type_de_jet`, `modificateurs`, `résultat`.

### 4.3 Gestion de version
- Chaque session : commit du nouvel état du monde et des journaux.
- Branches thématiques possibles (ex. `arc-2`, `pnj-serelune`).
- Tags pour marquer la fin de chaque arc/saison.

## 5. Personnages et classes
### 5.1 Création de personnage
- **Étapes** : concept, historique, classe, race, allocation de points, équipement de départ.
- **Races proposées** : Humain, Elfe des brumes, Nain runique, Tieffelin solaire, Demi-ondin, Goliath des pics.
- **Historique** : Loyalistes de Valoria, Exilés de Thorgar, Corsaires de Serelune, Mystiques de Khar'Seth, Erudits de l'Obélisque, Vagabonds libres.

### 5.2 Classes principales
1. **Lame d'Auralis** (guerrier tactique)
   - Compétences : Combat, Commandement, Défense.
   - Capacités : "Stratégie impériale" (+avantage tactique), "Mur de boucliers".
2. **Rôdeur des Brumes** (éclaireur et assassin)
   - Compétences : Déplacement, Crochetage, Survie.
   - Capacités : "Pas de brume", "Attaque perfide".
3. **Mage de Marée** (contrôle élémentaire)
   - Compétences : Magie, Connaissances, Dialogue mystique.
   - Capacités : "Flux et reflux", "Pacte des vagues".
4. **Clerc du Soleil Voilé** (prêtre-guerrier)
   - Compétences : Magie, Influence, Combat.
   - Capacités : "Ferveur solaire", "Bénédiction du voile".
5. **Forge-rune de Thorgar** (artisan combattant)
   - Compétences : Artisanat, Combat, Connaissances.
   - Capacités : "Armure vivante", "Rune adaptative".
6. **Vox Ombreuse** (barde-espion)
   - Compétences : Dialogue, Influence, Crochetage.
   - Capacités : "Voix du secret", "Masque des ombres".

### 5.3 Progression
- Niveaux 1 à 12 (progression par arc).
- Acquisition de talents à niveaux 3, 6, 9, 12 (talents généraux ou spécifiques à la classe).
- Points de domaines attribués à la création puis augmentés via l'expérience.

### 5.4 Alignements et motivations
- Utilisation d'un système de **Principes** (Fidélité, Ambition, Compassion, Pragmatique, Foi, Rébellion).
- Chaque principe a un score 0-3 influençant les réactions sociales et les tests de volonté.

## 6. Systèmes de jeu
### 6.1 Tests et jets de dés
- Base : **d20 + modificateurs**.
- Difficultés : 8 (simple), 12 (modéré), 16 (difficile), 20+ (héroïque).
- Avantage/désavantage : lancer 2d20, prendre le meilleur/pire.
- Jets de dégâts : dépendants de l'arme ou du sort (d6/d8/d10). L'agent gère les tirages et consigne les résultats.

### 6.2 Domaines
- Chaque domaine a un rang (Apprenti 0-1, Compétent 2-3, Maître 4-5).
- Influence directe sur :
  - Dialogue : négociations, persuasion.
  - Magie : lancer de sorts, résistance.
  - Combat : attaques, parades.
  - Déplacement : furtivité, acrobaties.
  - Crochetage : pièges, serrures.
  - Artisanat : fabrication, réparations.
  - Connaissances : lore, analyse.
  - Survie : navigation, résistance environnementale.
  - Influence : interactions politiques, commandement.

### 6.3 Combat
- Tours structurés (initiative via d20 + DEX/Domaine Combat).
- Actions : Attaque, Sort, Manœuvre, Soutien, Défense.
- Points de vie : calculés selon classe (ex. d10 pour Lame d'Auralis, d8 pour Vox Ombreuse).
- Conditions persistantes (Blessé, Épuisé, Corrompu par l'Ombre).

### 6.4 Magie et anomalies
- Sorts divisés en écoles : Flux (eau), Brume (illusion), Voile (lumière), Rune (renforcement), Ombre (danger).
- Zones d'anomalies : modificateurs aléatoires, risques d'explosion arcanique.

### 6.5 Exploration
- Cartes régionales avec points d'intérêt.
- Gestion de ressources (nourriture, matériaux, cristaux).
- Voyages influencés par saisons et état des routes.

### 6.6 Intrigues politiques
- Système de réputation par faction (-5 à +5).
- Événements déclencheurs lorsque des seuils sont atteints (alliance, embargo, assassinat).

### 6.7 Corruption de l'Ombre
- Jauge commune (0-10) mesurant l'influence de l'Ombre d'Ashkar.
- Augmente lors de sacrifices, échecs majeurs, usage de magie interdite.
- Effets à seuils (visions, apparition de monstres, transformation de PNJ).

## 7. Gestion de session
### 7.1 Préparation
- Lire `player_input.md` pour connaître les objectifs du joueur.
- Mettre à jour `sessions/<date>.json` avec :
  - `prelude`: résumé du contexte.
  - `goals`: objectifs déclarés.
  - `gm_notes`: complications préparées.

### 7.2 Déroulement
1. **Ouverture** : rappel des conséquences précédentes.
2. **Scène 1** : enjeu immédiat.
3. **Scène 2** : complication croissante.
4. **Scène 3** : confrontation majeure.
5. **Épilogue** : conséquences, hooks pour la suite.
6. **Synthèse** : consigner dans `docs/histoire_session_en_cours.md` les événements narratifs, jets notables et réponses aux questions du joueur.

### 7.3 Post-session
- Mettre à jour `world_state.json` (factions, régions, timeline).
- Mettre à jour fiches des personnages.
- Journaliser les jets de dés.
- Préparer le prochain cliffhanger dans `sessions/<date>.json`.

## 8. Format d'interaction joueur (`player_input.md`)
```
# Session YYYY-MM-DD
## Intentions
- Objectifs principaux
- Décisions tactiques
- PNJ à contacter

## Actions proposées
1. Description de l'action
   - Domaine/compétence envisagé(e)
   - Ressources à engager

## Questions pour le MJ
- Liste de questions ou doutes

## Réactions aux conséquences
- Choix proposés pour les suites
```
L'agent lit le fichier, interprète les intentions et réalise les jets de dés nécessaires.
À partir du nouveau mode d'itération :
- `player_input.md` sert de terminal de dialogue ; chaque réponse de l'agent inclut une version mise à jour du fichier qui formule clairement les choix offerts au joueur.
- Le joueur répond en éditant le fichier (ou en envoyant un message reprenant les champs demandés) et cette réponse devient le prompt de l'agent pour la scène suivante.
- Les sections peuvent être adaptées pour refléter la scène en cours (ex. remplacer "Actions proposées" par "Options immédiates"), mais doivent toujours expliciter les décisions attendues.

Chaque réponse de l'agent doit :
- traiter explicitement toutes les questions posées dans `player_input.md` ;
- actualiser les données pertinentes (état du monde, journaux, fiches) ;
- préparer un nouveau `player_input.md` focalisé sur la scène suivante avec des instructions claires de réponse.

## 9. Contenu additionnel
- **PNJ majeurs** : liste initiale (généraux, diplomates, espions, mentors) avec arcs personnels.
- **Objets légendaires** : Obélisque fragmenté, Lames runiques, Sphère des marées.
- **Quêtes secondaires** : libération d'esclaves, expéditions dans les ruines, infiltration de cultes.
- **Bestiaire** : monstres classiques et créatures corrompues (Spectres d'Ashkar, Léviathans des brumes, Titans des sables).

## 10. Exigences techniques
- Scripts Python (futurs) pour automatiser :
  - Lecture/écriture `player_input.md`.
  - Mise à jour des journaux de sessions.
  - Génération de résumés.
- Standards JSON et Markdown documentés.
- Consignation automatique des jets de dés avec seed si nécessaire pour reproductibilité.

## 11. Gouvernance du projet
- Utiliser issues GitHub pour suivre les tâches (ex. "Implémenter gestion de réputation").
- Relectures narratives pour chaque nouvel arc.
- Tests de cohérence : vérifier que les modifications de `world_state.json` s'alignent avec les événements décrits.

## 12. Prochaines étapes
1. Créer les fichiers de données initiales (`world_state.json`, `player_input.md`, `characters/`).
2. Définir la fiche du personnage joueur principal.
3. Établir les événements initiaux de l'Arc I dans `sessions/<date>.json`.
4. Mettre en place un script de gestion des jets de dés.

Ce document constitue la référence exhaustive pour le développement et la conduite de la campagne.
