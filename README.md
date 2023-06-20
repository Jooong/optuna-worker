# optuna-worker

[![PyPI - Version](https://img.shields.io/pypi/v/optuna-worker.svg)](https://pypi.org/project/optuna-worker)
[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/optuna-worker.svg)](https://pypi.org/project/optuna-worker)
[![GitHub Super-Linter](https://github.com/Jooong/optuna-worker/actions/workflows/lint.yaml/badge.svg)](https://github.com/marketplace/actions/super-linter)
[![Codecov](https://codecov.io/gh/Jooong/optuna-worker/branch/main/graph/badge.svg)](https://codecov.io/gh/Jooong/optuna-worker)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/python/black)

-----

`optuna-worker` is a python package to help using [optuna](https://github.com/optuna/optuna) without code modification to existing ML training project, with two assumptions.

1. You could pass hyperparameters to your trainer via cli arguments.
2. Metrics to be optimized are printed out as formatted logs during training.

A CLI named `optuna-worker` is included in this package, which runs optuna worker with a configuration yaml file.

```console
optuna-worker run $CONFIG_FILE
```

All it does is simply creating a proxy objective that

1. Creates a training subprocess, passing suggested parameters via CLI arguments.
2. Parses metric values from stdout of the training subprocess, so that they could be reported and returned.

Details of the configuration file could be found from the [documentation](./docs/configuration.md).
You can also find working example configuration files from [examples](./examples/).

## Installation

```console
pip install optuna-worker
```

## License

`optuna-worker` is distributed under the terms of the [MIT](https://spdx.org/licenses/MIT.html) license.
