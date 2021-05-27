---
id: "overview"
title: "Installing dbt"
---

dbt is a python program that can be installed locally for development. Your installation will differ based on the database, data lake, or query engine that you wish to use with dbt—we call those "adapters," and you can see [the full list](available-adapters).

If you know which adapter plugin you wish to use, we recommend installing that adapter specifically [using pip](install/pip#install-a-specific-adapter):

```
pip install dbt-postgres
```

If you're just getting started, or if don't know which adapter you'll be using, we recommend installing dbt using one of four tried-and-tested methods:

- [Homebrew](install/homebrew) (recommended for MacOS)
- [pip](install/pip)
- [Docker image](install/docker)
- [from source](install/from-source)
