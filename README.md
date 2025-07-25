# dbtdiff

[![PyPI version](https://img.shields.io/pypi/v/dbtdiff.svg)](https://pypi.org/project/dbtdiff/)
[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/dbtdiff.svg)](https://pypi.org/project/dbtdiff/)

A CLI tool to run dbt only on changed models with model+ chaining.

## Installation

```bash
pip install dbtdiff
```

## Features

The default behavior is to run `dbt build` on all downstream models that have changed since the last commit, using the `HEAD` reference. It supports:
- Custom commands (e.g., `dbt run`, `dbt test`)
- Custom targets
- Custom number of downstream models to include
- Ability to compare to `main` rather than your last commit.

## Usage

```bash
dbtdiff                        # Compare against last commit
dbtdiff -m                     # Compare against origin/main
dbtdiff -c run                 # Swap `build` for `run`, dbt run -t dev
dbtdiff -n 1                   # Run only run 1 downstream model
dbtdiff -t prod                # Use the prod target, eg: dbt build -t prod
dbtdiff -f                     # Include --full-refresh in the dbt command
```

All options can be combined, or fully qualified with `--command`, `--target`, `--number`, `--main` and `--full-refresh`.

## Quick QOL Roadmap

- Support for seeds
- Support for snapshots 
- Only run modified tests from .yml
- Custom branch names
- Macro change support