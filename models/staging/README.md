# 🥪 The Jaffle Shop 🦘

_powered by the dbt Fusion engine_

Welcome! This is a sandbox project for exploring the basic functionality of Fusion. It's based on a fictional restaurant called the Jaffle Shop that serves [jaffles](https://en.wikipedia.org/wiki/Pie_iron).

To get started:
1. Set up your database connection in `~/.dbt/profiles.yml`. If you got here by running `dbt init`, you should already be good to go.
2. Run `dbt build`. That's it!

## Python & dbt setup (recommended)

This repo works well with Python 3.11. A tested virtualenv is available at `~/.venv/jaffle-dbt-3.11`. You can also use the project `.venv` which has been recreated using Python 3.11 and contains a working dbt install.

To use the project venv:

```bash
# from the repo root
source .venv/bin/activate
# confirm dbt is available and the Postgres adapter is registered
dbt --version
dbt debug
```

If you'd rather use the isolated 3.11 venv created for testing:

```bash
source ~/.venv/jaffle-dbt-3.11/bin/activate
dbt --version
dbt debug
```

If you need to recreate the project venv with Python 3.11:

```bash
# Install python3.11 (Homebrew on macOS):
brew install python@3.11

# Recreate the project venv (from repo root):
/opt/homebrew/bin/python3.11 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip setuptools wheel
pip install dbt-core==1.10.15 dbt-postgres
```

## Example `profiles.yml` (place in `~/.dbt/profiles.yml`)

Copy this template and replace the placeholder values with your local Postgres credentials. Keep this file outside version control.

```yaml
jaffle_shop:
	target: dev
	outputs:
		dev:
			type: postgres
			host: localhost
			port: 5432
			user: jaffle        # replace
			password: jaffle    # replace
			dbname: jaffle      # replace or use 'database' depending on dbt version
			schema: jaffle
			threads: 4
```