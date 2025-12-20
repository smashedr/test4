[![PyPI Version](https://img.shields.io/pypi/v/toml-script?logo=pypi&logoColor=white&label=pypi)](https://pypi.org/project/toml-script/)
[![GitHub Release Version](https://img.shields.io/github/v/release/cssnr/toml-script?logo=github)](https://github.com/cssnr/toml-script/releases)
[![TOML Python Version](https://img.shields.io/badge/dynamic/toml?url=https%3A%2F%2Fraw.githubusercontent.com%2Fcssnr%2Ftoml-script%2Frefs%2Fheads%2Fmaster%2Fpyproject.toml&query=%24.project.requires-python&logo=python&logoColor=white&label=python)](https://github.com/cssnr/toml-script?tab=readme-ov-file#readme)
[![PyPI Downloads](https://img.shields.io/pypi/dm/toml-script?logo=pypi&logoColor=white)](https://pypistats.org/packages/toml-script)
[![Pepy Total Downloads](https://img.shields.io/pepy/dt/toml-script?logo=pypi&logoColor=white&label=total)](https://clickpy.clickhouse.com/dashboard/toml-script)
[![Codecov](https://codecov.io/gh/cssnr/toml-script/graph/badge.svg?token=A8NDHZ393X)](https://codecov.io/gh/cssnr/toml-script)
[![Workflow Lint](https://img.shields.io/github/actions/workflow/status/cssnr/toml-script/lint.yaml?logo=cachet&label=lint)](https://github.com/cssnr/toml-script/actions/workflows/lint.yaml)
[![Workflow Test](https://img.shields.io/github/actions/workflow/status/cssnr/toml-script/test.yaml?logo=cachet&label=test)](https://github.com/cssnr/toml-script/actions/workflows/test.yaml)
[![Deployment PyPi](https://img.shields.io/github/deployments/cssnr/toml-script/pypi?logo=pypi&logoColor=white&label=pypi)](https://pypi.org/project/toml-script/)
[![Deployment Docs](https://img.shields.io/github/deployments/cssnr/toml-script/docs?logo=materialformkdocs&logoColor=white&label=docs)](https://cssnr.github.io/toml-script/)
[![GitHub Last Commit](https://img.shields.io/github/last-commit/cssnr/toml-script?logo=github&label=updated)](https://github.com/cssnr/toml-script/pulse)
[![GitHub Repo Size](https://img.shields.io/github/repo-size/cssnr/toml-script?logo=bookstack&logoColor=white&label=repo%20size)](https://github.com/cssnr/toml-script)
[![GitHub Top Language](https://img.shields.io/github/languages/top/cssnr/toml-script?logo=htmx&logoColor=white)](https://github.com/cssnr/toml-script?tab=readme-ov-file#readme)
[![GitHub Contributors](https://img.shields.io/github/contributors-anon/cssnr/toml-script?logo=github)](https://github.com/cssnr/toml-script/graphs/contributors)
[![GitHub Issues](https://img.shields.io/github/issues/cssnr/toml-script?logo=github)](https://github.com/cssnr/toml-script/issues)
[![GitHub Discussions](https://img.shields.io/github/discussions/cssnr/toml-script?logo=github)](https://github.com/cssnr/toml-script/discussions)
[![GitHub Forks](https://img.shields.io/github/forks/cssnr/toml-script?style=flat&logo=github)](https://github.com/cssnr/toml-script/forks)
[![GitHub Repo Stars](https://img.shields.io/github/stars/cssnr/toml-script?style=flat&logo=github)](https://github.com/cssnr/toml-script/stargazers)
[![GitHub Org Stars](https://img.shields.io/github/stars/cssnr?style=flat&logo=github&label=org%20stars)](https://cssnr.github.io/)
[![Discord](https://img.shields.io/discord/899171661457293343?logo=discord&logoColor=white&label=discord&color=7289da)](https://discord.gg/wXy6m2X8wY)
[![Ko-fi](https://img.shields.io/badge/Ko--fi-72a5f2?logo=kofi&label=support)](https://ko-fi.com/cssnr)

# TOML Script

<a title="TOML Script" href="https://cssnr.github.io/toml-script/" target="_blank">
<img alt="TOML Script" align="right" width="128" height="auto" src="https://cssnr.github.io/toml-script/assets/images/logo.svg"></a>

- [Features](#features)
- [Install](#install)
- [Usage](#usage)
- [Support](#support)
- [Contributing](#contributing)

Define custom scripts in your pyproject.toml and easily run them with this dependency free tool.
This tool is both inspired by and similar to [NPM Scripts](https://docs.npmjs.com/cli/v8/using-npm/scripts).

If you run into any issues or have any questions, [support](#support) is available.

To get started [Install](#install) the cli and view the [Usage](#usage).

[![View Documentation](https://img.shields.io/badge/view_documentation-blue?style=for-the-badge&logo=googledocs&logoColor=white)](https://cssnr.github.io/toml-script/)

## Features<a id="features"></a>

- Define scripts in your `pyproject.toml`
- Easily run scripts with `run script`
- Cross-platform support using subprocess
- Supports multiple commands per script
- Supports `pre` and `post` scripts
- Automatically finds the `pyproject.toml`
- Runs scripts relative to the root directory
- Evaluate python code 🧪 (experimental)

## Install<a id="install"></a>

From PyPI: <https://pypi.org/p/toml-script>

```shell
pip install toml-script
uv tool install toml-script
# Add to Project
pip install --group dev toml-script
uv add --dev toml-script
```

[![View Install Guide](https://img.shields.io/badge/view_install_guide-blue?style=for-the-badge&logo=googledocs&logoColor=white)](https://cssnr.github.io/toml-script/cli/#install)

## Usage<a id="usage"></a>

First, add some scripts to the `pyproject.toml` using the `[tool.scripts]` section.

```toml title="pyproject.toml"
[tool.scripts]
clean = "rm -rf dist"
build = "run clean && uv run hatch build"
prelint = "echo always runs before lint"
lint = ["black --check .", "ruff check ."]
postlint = "echo always runs after lint"
format = """
black .
ruff format .
"""
cclean = "#py shutil.rmtree('.cache', True)"
```

[![View Scripts Guide](https://img.shields.io/badge/view_scripts_guide-blue?style=for-the-badge&logo=googledocs&logoColor=white)](https://cssnr.github.io/toml-script/cli/#scripts)

Run scripts with the `run` command.

```shell
run build
```

List available scripts with `--list`.

```shell
run -l
```

Run without installing using [astral-sh/uv](https://docs.astral.sh/uv/).

```shell
uvx toml-script build
```

[![View Usage Guide](https://img.shields.io/badge/view_usage_guide-blue?style=for-the-badge&logo=googledocs&logoColor=white)](https://cssnr.github.io/toml-script/cli/#usage)

## Support<a id="support"></a>

For general help or to request a feature, see:

- Q&A Discussion: <https://github.com/cssnr/toml-script/discussions/categories/q-a>
- Request a Feature: <https://github.com/cssnr/toml-script/issues/new?template=1-feature.yaml>
- Chat with us on Discord: <https://discord.gg/wXy6m2X8wY>

If you are experiencing an issue/bug or getting unexpected results, you can:

- Report an Issue: <https://github.com/cssnr/toml-script/issues>
- Chat with us on Discord: <https://discord.gg/wXy6m2X8wY>

[![Features](https://img.shields.io/badge/features-brightgreen?style=for-the-badge&logo=googleanalytics&logoColor=white)](https://github.com/cssnr/toml-script/issues/new?template=1-feature.yaml)
[![Issues](https://img.shields.io/badge/issues-red?style=for-the-badge&logo=southwestairlines&logoColor=white)](https://github.com/cssnr/toml-script/issues)
[![Discussions](https://img.shields.io/badge/discussions-blue?style=for-the-badge&logo=rocketdotchat&logoColor=white)](https://github.com/cssnr/toml-script/discussions)
[![Discord](https://img.shields.io/badge/discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/wXy6m2X8wY)

## Contributing<a id="contributing"></a>

If you would like to submit a PR, please review the [CONTRIBUTING.md](#contributing-ov-file).

Please consider making a donation to support the development of this project
and [additional](https://cssnr.com/) open source projects.

[![Ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/cssnr)

For a full list of current projects visit: [https://cssnr.github.io/](https://cssnr.github.io/)
