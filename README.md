# optuna-worker

[![PyPI - Version](https://img.shields.io/pypi/v/optuna-worker.svg)](https://pypi.org/project/optuna-worker)
[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/optuna-worker.svg)](https://www.python.org/)
[![GitHub Super-Linter](https://github.com/Jooong/optuna-worker/actions/workflows/lint.yaml/badge.svg)](https://github.com/marketplace/actions/super-linter)
[![Codecov](https://codecov.io/gh/Jooong/optuna-worker/branch/main/graph/badge.svg)](https://codecov.io/gh/Jooong/optuna-worker)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/python/black)

`optuna-worker` is a python package to help integrating [optuna](https://github.com/optuna/optuna) to your existing ML training project without code modification. With `optuna-worker`, you don't need to implement [objective function](https://optuna.readthedocs.io/en/stable/index.html#basic-concepts), but use your existing normal trainer. You could write a configuration YAML file and run optuna worker with a simple command.

```console
optuna-worker run $CONFIG_FILE
```

- Specification of the configuration file could be found from the [documentation](./docs/configuration.md)
- You could also refer to working [example configuration files](./examples/).

There are two assumptions on your trainer.

1. You could pass hyperparameters to your trainer via cli arguments.
2. Metrics to be optimized are printed out as formatted logs during training.

All it does is simply creating a proxy objective that

1. Creates a subprocess with a training command, passing suggested parameters via CLI arguments.
2. Parses metric values from stdout of the training subprocess, so that they could be reported and returned.

## Installation

```console
pip install optuna-worker
```

## License

`optuna-worker` is distributed under the terms of the [MIT](https://spdx.org/licenses/MIT.html) license.
