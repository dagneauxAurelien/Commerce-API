
![Tests](https://github.com/dagneauxAurelien/Commerce-API/actions/workflows/tests.yml/badge.svg) 
# Commerce API(Flask, SQLite) 
giving a company secure access to its sales
database, with JWT authentication and stock-safe order handling.

## Problem

A brand selling through short-video creators tracked sales in spreadsheets.
It could not tell which creators and videos brought customers, and a viral
video once triggered 400 orders for 30 units in stock.

## Features

- Relational model in 3NF (creators, videos, products, customers, orders, ad spend)
- Data pipeline: raw CSV -> one clean CSV per entity -> SQLite database
- JWT authentication, passwords hashed with bcrypt
- Stock can never go negative (409 when stock is too low)
- Test suite with pytest

## Data model
## Setup

```bash
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Build the database

```bash
python data/process_data.py    # generate the entity CSVs from data/raw/
python create_db.py            # create and populate data/tiktok.db
```

## Run the API

```bash
python app.py                  # serves on http://localhost:5000
```

## Run the tests

```bash
python run_tests.py                # the whole suite, question by question
```

Each test is reported with one of three marks: a green check (it passed), a
red cross (your code ran but produced a wrong result) or an hourglass (the
function or route is not written yet).

The results are grouped by question of the subject, and the runner also takes
arguments:

```bash
python run_tests.py 13             # only question 13
python run_tests.py 13 19 20       # several questions
python run_tests.py --failed       # only what is not done yet
python run_tests.py --traceback    # the full error of each problem
```

Giving a question number runs *only* that question's tests, which takes a
fraction of a second instead of the whole suite.
-rtual environment, the generated CSVs or `tiktok.db`:
`.gitignore` already excludes them.
