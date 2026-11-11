# D365 Environment Comparison Tool

An XrmToolBox tool that compares two Dynamics 365 / Dataverse environments (for example DEV and UAT) and lists the
configuration differences between them, ranked **ERROR**, **WARN** and **INFO**.

"Works in DEV, fails in UAT" is often configuration drift: a different solution version, an environment variable with
no value, an unbound connection reference, a disabled plugin step. This tool finds those differences for you.

## What it compares

Solutions, environment variables, connection references, plugin steps, web resources, business rules, classic
workflows, actions, business process flows and cloud flows.

## How to use it

1. Click **Select source** and **Select destination** and choose the two environments.
2. Tick one or more **publishers** and optionally one **solution** to limit the comparison.
3. Tick the **areas** to compare and press **Compare**.
4. Filter and search the results, and export the visible rows to CSV.

## Features

- Scope by publisher, solution and area; optional inclusion of managed components
- Findings ranked ERROR / WARN / INFO
- Explains why an item looks missing (for example "exists, but not in the compared scope; in solution X")
- Filter on every column, plus search
- Ignore list (JSON) that downgrades expected differences to INFO
- CSV export of the visible rows
- View difference (line comparison of a changed web resource or workflow) and saved profiles: new in 2.0, less tested

## Safe to use

Read-only: the tool only queries Dataverse and never changes either environment. It stores no credentials
(XrmToolBox owns the connections), and secret environment variable values are never retrieved.

## Requirements

XrmToolBox, a Windows PC, and read access to the two environments.

## Limitations

- Web resources and workflow definitions are compared by content hash; cloud flows by state only.
- Items outside the chosen publishers or solution are not compared.
- The tool reports differences; it cannot repair them.
