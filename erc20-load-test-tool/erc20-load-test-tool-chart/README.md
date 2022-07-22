# ERC20 Load Test Tool - Helm Chart

## Overview
This is a [helm chart](https://helm.sh) used for the deployment of erc20 load test tool on a [Kubernetes](https://kubernetes.io) environment.  

## Setup
Install the following tools
- [Helm v3](https://helm.sh/docs/intro/install/)

## Run
For running the erc20-load-test-tool-chart on a k8s cluster, update `erc20config.ethEndpoint.host` value in [values.yaml](./values.yaml) to point to the client node IP.
```bash
$ git clone https://github.com/vmware-samples/vmware-blockchain-samples.git
$ cd vmware-blockchain-samples/erc20-load-test-tool/erc20-load-test-tool-chart
$ helm install <benchmark-name> erc20-load-test-tool-chart
```
`benchmark-name` can be replaced with any unique value to keep track of different benchmarking runs.

## Cleanup
To clean up the resources created by the chart, run
```bash
$ helm uninstall <benchmark-name>
```
where `benchmark-name` is the release name used during the installation of the chart.
