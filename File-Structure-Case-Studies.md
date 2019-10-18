## Three examples of file structures for different project types

### [Case Study 1: Almost Flat](#casestudy1)

```
PROJECT/
├── figures/                                        <- plots.m saves figures in here 
├── main.m                                          <- does something fancy, calls plots.m
├── plots.m  																				<- make presentation figures
├── raw2wind.m                                      <- script to clean .csv data to .mat 
├── readme.txt
├── windSpeed_MITGreenBuilding.mat                  <- cleaned data
├── weatherStation_MITGreenBuilding_2019_07_01.csv  <- raw data
├── weatherStation_MITGreenBuilding_2019_07_02.csv
├── weatherStation_MITGreenBuilding_2019_07_03.csv
├── weatherStation_MITGreenBuilding_2019_07_04.csv
├── weatherStation_MITGreenBuilding_2019_07_05.csv
├── weatherStation_MITGreenBuilding_2019_07_06.csv
└── weatherStation_MITGreenBuilding_2019_07_07.csv
```

### [Case Study 2: A Simple Hierarchy](#casestudy2)

```
PROJECT/
├── bin/            <- compiled binaries. 
├── data/ 
│   ├── raw/
│   └── clean/
│
├── figures/        <- figures used in place of a "results" folder. 
├── scripts/
│   ├── process/    <- scripts to maniuplate data between raw, cleaned, final stages.
│   └── plot/	      <- intermediate plotting.
│
├── src
│   ├── model1/     <- various experimental models.
│   ├── model2/
│   └── model3/
│
├── LICENSE
├── Makefile
└── readme.md
```

### [Case Study 3: A Complex Hierarchy](#casestudy3)

This example is borrowed from [cookiecutter data science](https://drivendata.github.io/cookiecutter-data-science/).

```
PROJECT/
├── LICENSE
├── Makefile           <- Makefile with commands like `make data` or `make train`
├── README.md          <- The top-level README for developers using this project.
├── data/
│   ├── external/      <- Data from third party sources.
│   ├── interim/       <- Intermediate data that has been transformed.
│   ├── processed/     <- The final, canonical data sets for modeling.
│   └── raw/           <- The original, immutable data dump.
│
├── docs/              <- A default Sphinx project; see sphinx-doc.org for details
│
├── models/            <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks/         <- Jupyter notebooks. Naming convention is a number (for ordering),
│                         the creator's initials, and a short `-` delimited description, e.g.
│                         `1.0-jqp-initial-data-exploration`.
│
├── references/        <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports/           <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures/       <- Generated graphics and figures to be used in reporting
│
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
│
├── setup.py           <- Make this project pip installable with `pip install -e`
├── src/               <- Source code for use in this project.
│   ├── __init__.py    <- Makes src a Python module
│   │
│   ├── data/          <- Scripts to download or generate data
│   │   └── make_dataset.py
│   │
│   ├── features/      <- Scripts to turn raw data into features for modeling
│   │   └── build_features.py
│   │
│   ├── models/        <- Scripts to train models and then use trained models to make
│   │   │                 predictions
│   │   ├── predict_model.py
│   │   └── train_model.py
│   │
│   └── visualization/ <- Scripts to create exploratory and results oriented visualizations
│       └── visualize.py
│
└── tox.ini            <- tox file with settings for running tox; see tox.testrun.org
```
