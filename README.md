# OB_LONGREAD_GERMLINE_SV_CALLERS_BENCHMARK-main

This repository contains the code to reproduce our analysis from:

"Benchmarking long-read germline structural variant callers for research and clinic using both linear and pangenome-graph references with a novel dataset"

## Overview 

![Workflow image](images/workflow.png)

## How to run

Please clone this repository using ```--recurse-submodules``` in order to automatically clone the submodules that are necessary for running this benchmark, which is orchestrated by Omnibenchmark and has been tested and validated using Omnibenchmark v0.5.0. The following command can be used to run the workflow for PacBio HiFi and ONT data, respectively:

```sh
# PacBio HiFi
ob run benchmark_truthset_pacbio.yaml \
 --rerun-triggers input mtime \
 --out-dir pacbio_results \
 --dirty \
 --singularity-args \
 "--bind /paths/to/bind"
 --workflow-profile /path/to/workflow-profile

# ONT
ob run benchmark_truthset_ont.yaml \
 --rerun-triggers input mtime \
 --out-dir ont_results \
 --dirty \
 --singularity-args \
 "--bind /paths/to/bind"
 --workflow-profile /path/to/workflow-profile
```

This commands will start a snakemake pipeline that will produce the benchmarking results under the folders ```pacbio_results``` and ```ont_results```.
