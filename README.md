# Texte Mining BE

- Tariq CHELLALI
- 07/04/2024


Voici un résumé  des scores des différents modèles de classification appliqué à la base **movie_reviews** :

| Modèles                                                 | score |
|--------------------------------------------------------|-------------|
| DecisionTreeClassifier (arbre de décision)                  | 0.7291     |
| Random Forest                 |0.8357                         |
| Modèle linéaire (LogisticRegression)                   | 0.8379      |
| Evaluation : ROC de RF                | AUC = 0.8379     |
| Multinomial Bayesian (MNB)                             | 0.8338      |
| RandomForest                                           | 0.8396      |
| RandomForestClassifier (n_estimators=150, max_depth=90)| 0.8461      |
| RandomForestClassifier (n_estimators=100, max_depth=70)| 0.8471      |
| Gradient Boost | 0.5688     |
| SVM linéaire avec OneVsRestClassifier                  | 0.8968      |
| LogisticRegression avec données lemmatisées (bi-gramme)| 0.8987      |
| LogisticRegression avec Cross-validation  les données de base            | 0.9162      |
| MultinomialNB sur les données de base                  | 0.8862      |
| MNB avec Validation Croisée (XV)                       | 0.8868      |
| RandomForestClassifier avec SVD                        | 0.7139      |
| LogisticRegression avec SVD                            | 0.7944      |
| TF-IDF -> SVD -> LogisticRegression                    | 0.8769      |
| LogisticRegression sur word2vect  (model gensim)                     | 0.6219      |
| LogisticRegression sur word2vect (modele pré-entrainé de google)    | 0.8336      |
| RandomForest sur word2vect (modele pré-entrainé de google)    | 0.7934      |
| SVM sur word2vect (modele pré-entrainé de google)    | 0.8477      |
| MLPClassifier sur word2vect (modele pré-entrainé de google)    | 0.841      |

Nous remarquons que :

| Description          | Modèle                                     | Performance |
|----------------------|--------------------------------------------|-------------|
| Performance maximale | LogisticRegression avec Cross-validation les données de base   | **0.9162**      |
| Performance minimale | LogisticRegression sur word2vect (model gensim)          | **0.6219**      |


 Voici quelques observations et commentaires sur les résultats :

- **Haute performance avec la régression logistique :** Il est remarquable que la régression logistique, en particulier avec la validation croisée et les données de base, obtienne les meilleures performances (0.9162). Cela souligne l'efficacité de la régression logistique pour les tâches de classification textuelle, surtout lorsqu'elle est combinée avec des techniques de validation robustes.

- **L'importance de la validation croisée :** L'amélioration notable des scores lors de l'utilisation de la validation croisée (cross-validation) indique son importance pour obtenir une estimation plus fiable et robuste de la performance du modèle.

- **Les modèles basés sur des arbres :** Les Random Forests montrent de bonnes performances, en particulier avec des hyperparamètres ajustés (n_estimators et max_depth). Cela illustre l'importance de l'ajustement des hyperparamètres dans l'amélioration des performances des modèles.

- **Le SVM linéaire se démarque :** Le SVM linéaire avec OneVsRestClassifier obtient un score élevé (0.8968), ce qui met en évidence sa capacité à gérer des tâches de classification multiclasse efficacement.

- **Difficultés avec Gradient Boosting :** Le Gradient Boosting a montré une performance relativement faible (0.5688). Cela peut indiquer que le modèle est soit surajusté, soit sous-ajusté, ou que l'ensemble de données n'est pas adapté pour ce type de modèle dans sa forme actuelle.

- **Word2Vec et performances :** L'utilisation de word2vec (en particulier le modèle pré-entraîné de Google) a donné des résultats mixtes. Bien que meilleure que le modèle généré avec Gensim, sa performance reste inférieure à celle de la régression logistique avec des données lemmatisées ou des features traditionnels comme TF-IDF. Cela peut suggérer que pour cette tâche spécifique, les caractéristiques contextuelles capturées par Word2Vec ne sont pas aussi cruciales que les caractéristiques sémantiques ou syntaxiques plus directes.

- **Performance minimale :** La performance la plus faible obtenue avec la régression logistique sur les vecteurs Word2Vec (0.6219) suggère que le modèle n'a pas réussi à capturer suffisamment bien les nuances sémantiques ou que le processus de vectorisation n'a pas été optimal.
