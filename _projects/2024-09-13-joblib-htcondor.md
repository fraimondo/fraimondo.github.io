---
title: 'joblib-htcondor'
subtitle: 'An HTCondor backend for joblib'
date: 2024-09-13 00:00:00
featured_image: /images/fraimondo/rio_v.jpeg
project_image: '/images/projects/joblib_htcondor_logo.svg'
image_size: contain
excerpt: Run joblib-parallelised Python code, including scikit-learn, on an HTCondor cluster, with each task submitted as its own job.
publish: true
---

joblib-htcondor is a [joblib](https://joblib.readthedocs.io) backend that sends each task to an [HTCondor](https://htcondor.org) cluster as a separate job. Code that already uses joblib, such as scikit-learn's cross-validation and hyperparameter search, can scale out to a whole cluster with very few changes:

```python
from operator import neg
from joblib import Parallel, delayed, parallel_config
from joblib_htcondor import register_htcondor

register_htcondor()

with parallel_config(
    backend="htcondor",
    n_jobs=-1,
    request_cpus=1,
    request_memory="1Gb",
):
    Parallel()(delayed(neg)(i + 1) for i in range(5))
```

Tasks and results go through a disk shared by all the nodes, so the backend works best for many compute-heavy tasks rather than short or I/O-bound ones.

```
pip install joblib-htcondor
```

- [Source code on GitHub](https://github.com/juaml/joblib-htcondor)
