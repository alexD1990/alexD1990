<h1 align="center">Alex</h1>
<p align="center"><b>Data engineer × AI agent tooling</b><br>
Databricks, Spark and dbt — and the MCP tooling that gives AI assistants real context.</p>

<p align="center">
  <img src="https://skillicons.dev/icons?i=python,go,ts,docker,git,githubactions,linux,vscode&theme=dark" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Databricks-FF3621?style=for-the-badge&logo=databricks&logoColor=white" />
  <img src="https://img.shields.io/badge/Apache_Spark-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white" />
  <img src="https://img.shields.io/badge/dbt-FF694B?style=for-the-badge&logo=dbt&logoColor=white" />
  <img src="https://img.shields.io/badge/Delta_Lake-00ADD4?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Unity_Catalog-1F2937?style=for-the-badge" />
  <img src="https://img.shields.io/badge/MCP-6B7280?style=for-the-badge" />
</p>

---

I'm a data engineer in Norway, working on Databricks with Spark and dbt. Most of the tools
I build exist because something in a pipeline was hard to see — what a table actually
contains, or where in a dbt DAG a row went missing. Alongside that I build agent tooling:
MCP servers and a package manager for them, because AI assistants are only as useful as
the context they get. Most of what's below is published and installable.

## What I do

**Data engineering**

- **Data platforms on Databricks** — ingestion, Unity Catalog, and layered models with dbt
- **dbt projects** — structure, conventions and tests from the first model
- **Data quality and observability** — knowing what is in a table before anyone relies on it
- **Pipeline debugging** — lineage, row-level tracing and table history when numbers don't add up

**AI agent tooling**

- **MCP servers and integrations** that give AI assistants structured access to code and data
- **Developer tooling in Go, Python and TypeScript**, shipped to PyPI and the VS Code Marketplace

## Data engineering

### [zynex](https://github.com/alexD1990/zynex) &nbsp;[![PyPI](https://img.shields.io/pypi/v/zynex?style=flat&logo=pypi&logoColor=white&label=PyPI)](https://pypi.org/project/zynex/)
Notebook-first data quality checks for Spark and Databricks. One call — `zx("schema.table")` —
checks duplicates, null ratios, skew and small Delta files, and prints a readable report.

### [dataowl](https://github.com/alexD1990/dataowl) &nbsp;[![PyPI](https://img.shields.io/pypi/v/dataowl?style=flat&logo=pypi&logoColor=white&label=PyPI)](https://pypi.org/project/dataowl/)
Read-only inspector for Spark and Delta tables. Collects the facts about a table — row counts,
keys, constraints, columns, timestamps, properties and history — and renders them as a clear
overview in the terminal. It describes the data; it does not judge it.

### [DAGtracer](https://github.com/alexD1990/DAGtracer) &nbsp;![dbt](https://img.shields.io/badge/dbt-FF694B?style=flat&logo=dbt&logoColor=white)
Finds where a row disappears in a dbt DAG. Give it a key, a value and a starting model —
`dgt orgnr,222,mart_summary` — and it walks upstream until it reaches the model where the row
stops existing. Output as text, JSON or NDJSON.

### [dbt-databricks-template](https://github.com/alexD1990/dbt-databricks-template) &nbsp;![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=flat&logo=databricks&logoColor=white)
Starter template for dbt projects on Databricks with Unity Catalog, so a new project starts
from conventions instead of an empty folder.

## AI agent tooling

### [arcmesh-pm](https://github.com/alexD1990/arcmesh-pm) &nbsp;![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white) [![Install](https://img.shields.io/badge/install-script-2EA44F?style=flat)](https://github.com/alexD1990/arcmesh-pm#install)
The package manager for MCP servers. `apm install github` finds the server, prompts for secrets
and configures Claude Desktop, VS Code, Cursor or Windsurf. Falls back to the official MCP
Registry, and on WSL wraps servers automatically so Windows clients can reach them.

### [arcmesh-cli](https://github.com/alexD1990/arcmesh-cli) &nbsp;[![PyPI](https://img.shields.io/pypi/v/arcmesh?style=flat&logo=pypi&logoColor=white&label=PyPI)](https://pypi.org/project/arcmesh/)
One command to make a codebase AI-ready. Sets up the MCP context an assistant needs to
understand a project, without hand-written config.

### [arcmesh-extension](https://github.com/alexD1990/arcmesh-extension) &nbsp;[![VS Code Marketplace](https://img.shields.io/visual-studio-marketplace/v/arcmesh.arcmesh?style=flat&logo=visualstudiocode&logoColor=white&label=Marketplace)](https://marketplace.visualstudio.com/items?itemName=arcmesh.arcmesh)
VS Code extension that gives AI assistants persistent project context. Runs a local MCP server
that exposes architecture notes, decisions and component docs, plus code search and git
history (log, diff, blame).

### [arcmesh-registry](https://github.com/alexD1990/arcmesh-registry) &nbsp;![JSON Schema](https://img.shields.io/badge/JSON_Schema-000000?style=flat&logo=json&logoColor=white)
File-based registry of MCP servers — one schema-validated `manifest.json` per server, no
database and no API. `arcmesh-pm` reads it directly from GitHub.

## How I work

- **Look before you trust.** Profile a table before building on it — row counts, keys, nulls and history first, models second.
- **Tools describe, engineers decide.** My tools report what they found, not what you should feel about it. The judgement stays with the person who knows the context.
- **Read-only by default.** Anything that touches someone else's data starts without write access, and earns it later if it needs it.
- **Metadata before compute.** Delta history and file layout are free information — read them before scanning a billion rows.
- **One command, or it won't get used.** `zx("schema.table")`, `apm install github`. If a tool needs a setup guide, it needs more work.
- **Ship it.** If something is useful to me, it goes on PyPI or the Marketplace so others can install it in one line.

## Currently

- Growing **dataowl** — more facts about Spark and Delta tables, same rules: read-only, no judgement
- Bringing my two tracks together: giving AI assistants real context about data platforms — lineage, table facts and dbt models — through MCP, so they can reason about pipelines instead of guessing

---

<p align="center">
  <a href="https://www.linkedin.com/in/alexandro-drønnen-a17a5711a/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
  <a href="mailto:alex12060309@gmail.com"><img src="https://img.shields.io/badge/Email-333333?style=for-the-badge&logo=maildotru&logoColor=white" /></a>
</p>
<p align="center">Norway · Open to conversations about data platforms and AI agent tooling</p>
