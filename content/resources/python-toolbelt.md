---
title | "Python Toolbelt"
# menu | "main" # add link at top of home page
---

## editing

| use case          | tools     |
| ----------------- | --------- |
| editor            | astronvim |
| jupyter notebooks | vscodium  |

## language checks

| use case        | tools                                              |
| --------------- | -------------------------------------------------- |
| language server | pyright + ruff-lsp                                 |
| type checking   | pyright                                            |
| linting         | ruff                                               |
| formatting      | black (i don't quite like it, but it seems futile) |

## project setup

| use case             | tools                |
| -------------------- | -------------------- |
| templating           | huak                 |
| virtual environments | venv                 |
| package management   | pip                  |
| package backend      | hatchling (via huak) |
| package frontend     | build (via huak)     |
| package publishing   | twine (via huak)     |

## libraries / frameworks

| use case         | tools                   |
| ---------------- | ----------------------- |
| api              | fastapi -> litestar     |
| async            | trio                    |
| cli              | typer, rich             |
| data analysis    | numpy, pandas -> polars |
| files            | pathlib                 |
| gui              | gooey                   |
| http             | httpx                   |
| images           | pillow                  |
| logging          | structlog               |
| nlp              | spacy, nltk             |
| plotting         | seaborn                 |
| pyobject storage | shelve                  |
| scraping         | scrapy, beautifulsoup   |
| space            | astropy                 |
| templating       | jinja                   |
| time             | arrow                   |

## testing

| use case        | tools       |
| --------------- | ----------- |
| test framework  | pytest      |
| test automation | nox?        |
| coverage        | coverage.py |

## documentation

| use case       | tools           |
| -------------- | --------------- |
| docs framework | **TODO**        |
| release notes  | release-drafter |
