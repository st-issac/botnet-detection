### Rough Outline

The goal for this phase is to develop a comparative supervised pipeline (testing a number of supervised classifiers). It should produce a single experiment runner with multiple models, one of which can be selected at a time. 

The pipeline is to be something like:
1. **Data access:** Load dataset, define feature columns, define tagrte.
2. **Split definition:** Fixed train/test split for comparison across classifiers.
3. **Preprocessing:** Transforming inputs in a model-compatible way (e.g. one-hot encoding for categorical features, scaling for numerical feature, etc.).
4. **Model definition:** Instantiate classifiers and store in a clearly accessibly registry.
5. **Evaluation + results:** Compute a selection of metrics consistently for each model and save outputs.

The folder structure I have currently is:
```
botnet_detection/
│
├── data/
│   └── raw/                  
│
├── notebooks/
│   └── exploration.ipynb
│
├── notes/
|
├── results/
│   ├── figures/
│   ├── metrics/
│   └── predictions/
|
├── scripts/
│   └── run_compare_models.py
|
├── src/
|   ├── __init__.py
│   ├── config.py
│   ├── data.py
│   ├── evaluation.py
│   ├── experiment.py
│   ├── features.py
│   └── models.py
│
├── venv/
│
├── .gitignore
├── README.md
└── requirements.txt
```

### Rough Details

Looking at the `\src` files:
- `__init__.py`: Apparently serves to declare the folder it is within (`\src` in this case?) as a package, which can then be imported (alongside specific functions and such inside it).
    - Apparently adding code within it can mean that it can run code within the file if I import the folder. So if the file contained `variable = 42` and I did `import src` and then `src.variable`, it would return `42`.

- `config.py`: Contains constants and experiment settings for the experiment. 
    - Things like hyperparameter values for various models (in `models.py` I assume) come to mind. Perhaps also stuff like `42` for `random_seed`, train/test split, selected input features and output as well? 
    - I do wonder if some parts of this could simply be defined in the other .py files themselves.

- `data.py`: Loading the dataset and selecting the relevant columns to use for inputs and outputs. Perhaps this is where the problem can be turned into a binary classification one (adjusting the labels to be 0 and 1 for benign and botnet flows respectively).

- `evaluation.py`: Selection of evaluation metrics, perhaps as a function to run simply in the experiment.

- `experiment.py`: Pulling together parts from various files (load data, train/test split, preprocess, fit and predict, evaluate, collect results).

- `features.py`: Preprcoessing bits? Not too sure about this one.

- `models.py`: Defines the selectiosn of models to use. I think they would all be instantiated here? (I.e. not just a dictionary with model names.)

These all seem useful, I'm simply not used to this kind of folder structure (although I'm sure it will be helpful once code is properly underway).
