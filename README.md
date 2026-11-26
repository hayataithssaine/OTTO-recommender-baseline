# OTTO-recommender-baseline
Baseline pour la compétition Kaggle OTTO (late submission) : articles récents + populaires
# OTTO Multi-Objective Recommender System : baseline

Late submission sur Kaggle : https://www.kaggle.com/competitions/otto-recommender-system

## Tâche
Pour chaque session du test, prédire 20 articles pour 3 actions
(clicks, carts, orders). Métrique : Recall@20 pondéré
(0.10 clicks, 0.30 carts, 0.60 orders).

## Méthode (baseline)
- **clicks** : derniers articles vus dans la session (sans doublons)
- **carts / orders** : d'abord les articles déjà ajoutés au panier ou commandés,
  puis les derniers articles vus
- Si la session a moins de 20 articles : complétion avec les 20 articles
  les plus fréquents du test
- Lecture de `test.jsonl` ligne par ligne (économie de RAM)

## Résultats
| | Score |
|---|---|
| Private | 0.49012 |
| Public | 0.48868 |

Il s'agit d'une *late submission* (compétition terminée en février 2023),
donc le score n'apparaît pas dans le classement officiel.
Capture : `kaggle_score_otto.png`

## Pistes d'amélioration
- Matrices de co-visitation (méthode classique sur cette compétition)
- Pondération par récence et par type d'action
- Modèle de reranking (XGBoost) sur des candidats générés
