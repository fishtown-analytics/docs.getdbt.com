---
datatype: [directorypath]
default_value: [target_path]
---

<File name='dbt_project.yml'>

```yml
clean-targets: [directorypath]
```

</File>


## Definition
Optionally specify a custom list of directories to be removed by the `dbt clean` [command](clean). As such, you should only include directories containing artifacts (e.g. compiled files, logs, installed packages) in this list.

## Default
If this configuration is not included in your `dbt_project.yml` file, the `clean` command will remove files in your [target-path](target-path).

## Examples
### Remove packages and compiled files as part of `dbt clean`
:::info
This is our preferred configuration
:::
To remove packages as well as compiled files, include the value of your [modules-path](modules-path) configuration in your `clean-targets` configuration.

<File name='dbt_project.yml'>

```yml
clean-targets:
    - target
    - dbt_modules
```

</File>

Now, run `dbt clean`.

Both the `target` and `dbt_modules` directory will be removed.

Note: this is the configuration in the dbt [starter project](https://github.com/fishtown-analytics/dbt-starter-project/blob/master/dbt_project.yml), which is generated by the `init` command.


### Remove `logs` when running `dbt clean`

<File name='dbt_project.yml'>

```yml
clean-targets: [target, dbt_modules, logs]

```

</File>