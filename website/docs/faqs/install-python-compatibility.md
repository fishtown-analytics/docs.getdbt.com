---
title: What version of python can I use?
---

`dbt-core` is compatible with Python versions 3.6 and higher, including python 3.9.

Some adapter plugins may have dependencies that are not compatible with the latest version of python. For example, dbt-snowflake v0.19 is not compatible with python 3.9, but dbt-snowflake v0.20 will be.

As of v0.15.0, dbt is no longer compatible with Python2.
