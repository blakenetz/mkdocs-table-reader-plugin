---
hide:
  - navigation
---

# Options

You can customize the plugin by setting options in `mkdocs.yml`. For example:

```yml
plugins:
  - table-reader:
      base_path: "config_dir"
      data_path: "."
      search_page_directory: True
      allow_missing_files: False
      select_readers:
        - read_csv
        - read_json
```

## `base_path`

The base path where `mkdocs-table-reader-plugin` will search for input files. The path to your table files should be relative to the `base_path`. Allowed values:

- `config_dir` (default): the directory where your project's `mkdocs.yml` file is located.
- `docs_dir`: the directory where your projects' `docs/` folder is located.

If you store your table in `docs/assets/table.csv`, you can insert it in any markdown page using <code>\{\{ read_csv("docs/assets/table.csv") \}\}</code>, or when `base_path` is `docs_dir`, with <code>\{\{ read_csv("assets/table.csv") \}\}</code>.

!!! info

    Note that by default the plugin will _also_ search the page's directory but only when a table is not found.

    For more examples see the how to guide on [project structure](howto/project_structure.md).

## `data_path`

The path to your table files should be relative to the `base_path`. If you use a folder for all your table files you can shorten the path specification by setting the `data_path`.

For example, if your table is located in `docs/tables/basic_table.csv`, you can set `data_path` to `docs/tables/` and leave `base_path` to the default `config_dir`. Then you will be able to use <code>\{\{ read_csv("basic_table.csv") \}\}</code> instead of <code>\{\{ read_csv("docs/tables/basic_table.csv") \}\}</code> inside any markdown page.

Default is `.`, which means you need to specify the path to your table files relative to the `base_path`.

!!! info

    Note that by default the plugin will _also_ search the page's directory but only when a table is not found.

    For more examples see the how to guide on [project structure](howto/project_structure.md).

## `search_page_directory`

Default: `True`. When enabled, if a filepath is not found, the plugin will also attempt to find the file relative to the current page's directory.

!!! info

    Note that even when `True`, the path relative to `data_path` is searched first,
    and if a file is not found there, then the page's directory is searched.

    For more examples see the how to guide on [project structure](howto/project_structure.md).

## `allow_missing_files`

Default: `False`. When enabled, if a filepath is not found, the plugin will raise a warning instead of an error.

## `select_readers`
Default: Select all available readers. To increase performance, only the used readers can be specified. 
