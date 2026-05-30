---
name: add-combo-table
description: Instructions for generating a new table of character combos.
disable-model-invocation: true
---

When given a filepath to a .csv file, a markdown file in the project, and a specific line in the markdown file, create a markdown table on that line with the column names `Combo`, `Damage`, `Advantage`, and `Notes`.

Excluding the header, copy each row in the .csv file to its corresponding row in the table.

Reference for markdown syntax for tables: https://www.markdownguide.org/extended-syntax/#tables