# Risque de défaut de crédit

Prédire la probabilité qu'un demandeur de crédit fasse défaut, à partir de son profil : revenu, âge, ancienneté professionnelle, situation matrimoniale, statut de logement, profession, ville et État.

**252 000 dossiers**, dont **12,3 % de clients à risque** et 87,7 % de clients sains.

## Le vrai problème : le déséquilibre

Ce rapport de 1 à 7 est ce qui rend l'exercice intéressant, et ce qui piège les modèles naïfs.

Un classifieur qui répondrait « sain » à tout le monde afficherait **87,7 % de justesse**. Le chiffre est flatteur et le modèle est inutile : il ne détecte aucun défaut, c'est-à-dire précisément ce qu'on lui demande.

C'est pourquoi la justesse est écartée comme critère, au profit du rappel sur la classe minoritaire, de la précision, et de l'aire sous la courbe ROC.

**SMOTE** est utilisé pour rééquilibrer : la technique fabrique de nouveaux exemples de la classe minoritaire en interpolant entre voisins proches, plutôt que de dupliquer bêtement les existants. Point de méthode important : le rééchantillonnage ne s'applique qu'au jeu d'entraînement. L'appliquer avant le découpage ferait fuiter des exemples synthétiques dans le test et gonflerait artificiellement les scores.

## Démarche

1. **Exploration** — distribution des variables numériques et catégorielles, croisement avec le défaut.
2. **Préparation** — encodage des catégorielles, mise à l'échelle des numériques.
3. **Rééquilibrage** — SMOTE sur le seul jeu d'entraînement.
4. **Modélisation** — plusieurs classifieurs entraînés et comparés.
5. **Évaluation** — matrice de confusion, précision, rappel, F1 et ROC.

## Contenu du dépôt

| Fichier | Rôle |
| --- | --- |
| `Loan_Default_Risk_Analysis_and_Prediction.ipynb` | L'analyse complète |
| `Training Data.csv` | Jeu d'entraînement |
| `Test Data.csv` | Jeu de test |

## Exécution

```bash
pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn
jupyter notebook Loan_Default_Risk_Analysis_and_Prediction.ipynb
```

## L'arbitrage qui reste à trancher

Aucun seuil n'est bon dans l'absolu : tout dépend du coût relatif des deux erreurs.

Accorder un prêt à un mauvais payeur coûte le capital. Refuser un bon client coûte une marge. Ces deux montants ne sont pas du même ordre, et c'est la banque, pas le modèle, qui doit dire lequel pèse le plus. Le travail suivant consisterait à traduire ce coût en seuil de décision, plutôt que de s'en tenir au 0,5 par défaut.
