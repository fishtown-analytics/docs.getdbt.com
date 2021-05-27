---
title: "Homebrew"
---

### Installation

Install [Homebrew](http://brew.sh/). Then run:

```shell
brew update
brew install git
brew tap fishtown-analytics/dbt
brew install dbt
```

Homebrew will install `dbt-core` and the four most popular adapter plugins. Test your installation with `dbt --version`:

```
$ dbt --version
installed version: 0.19.1
   latest version: 0.19.1

Up to date!

Plugins:
  - bigquery: 0.19.1
  - snowflake: 0.19.1
  - redshift: 0.19.1
  - postgres: 0.19.1
```

### Upgrading

To upgrade dbt, use:

```shell
brew update
brew upgrade dbt
```

### Switching versions

You can install and use multiple versions of dbt with Homebrew through something called Homebrew "links." To allow installation of another version of dbt, first unlink the current version:

```shell
brew unlink dbt
brew install dbt@0.19.0
brew link dbt@0.19.0
```

Now, you can use dbt version 0.19.0:

```
$ dbt --version
installed version: 0.19.0
   latest version: 0.19.0

Up to date!

Plugins:
  - bigquery: 0.19.0
  - snowflake: 0.19.0
  - redshift: 0.19.0
  - postgres: 0.19.0
```

You can switch between versions by linking the one you want to use:

```shell
brew unlink dbt@0.19.0
brew link dbt
```

If you want to use the latest development version of dbt, you can install it as follows:

```shell
brew unlink dbt
brew update
brew install dbt-development
brew link dbt-development
```
