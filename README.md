# Iris species predictor

Small web app for a Weka assignment. A J48 decision tree is trained on the iris
dataset, and the app predicts the iris species from petal measurements.

**Live demo:** https://gren-95.github.io/weka-iris-app/

## Files

| File | What it is |
|------|------------|
| `iris.arff` | Training data (150 rows, 4 features, 3 classes). |
| `weka-output.txt` | Weka J48 training + 10-fold cross-validation output. |
| `index.html` | The app. Reads the two files above and parses the tree at runtime. |

## Run it

The app loads the files with `fetch`, so it needs a web server (it will not work
from `file://`):

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000 — or just use the live demo above.

## Model

J48 decision tree (Weka's C4.5), trained in Weka 3.8.6 with 10-fold
cross-validation, 96% accuracy. The tree uses only petal length and petal width.

Trained with:

```bash
java -cp weka.jar weka.classifiers.trees.J48 -t iris.arff > weka-output.txt
```
