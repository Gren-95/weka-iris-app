# Iris species predictor — Weka assignment

Machine learning model trained in Weka, plus a web app that asks the user for
measurements and outputs a predicted iris species.

## Files

| File | Purpose |
|------|---------|
| `iris.arff` | Training data (150 instances, 4 numeric features, 3 classes). |
| `weka-output.txt` | Weka training and 10-fold cross-validation output (J48 classifier). |
| `index.html` | The application: a self-contained web page. No server needed. |

## Model

- Algorithm: J48 decision tree (Weka implementation of C4.5).
- Validation: stratified 10-fold cross-validation.
- Accuracy: 96% (144/150 correctly classified on cross-validation).

The trained tree uses only petal length and petal width. The Weka J48 output is
embedded verbatim in `index.html` and parsed at runtime into a decision tree, so
retraining only means replacing that text — no branch logic is hand-written.

## How the model was trained

```bash
java -cp weka.jar weka.classifiers.trees.J48 -t iris.arff > weka-output.txt
```

(Weka 3.8.6; `-t` trains on the file and runs 10-fold cross-validation by default.)

## Run the app

Open `index.html` in any web browser. Enter petal length and petal width (cm) —
the only features the tree uses — and press "Ennusta liik". The page shows the
predicted species and the decision path the tree followed.
