# governor
[![Build Status](https://travis-ci.org/keikoproj/governor.svg?branch=master)](https://travis-ci.org/keikoproj/governor)
[![codecov](https://codecov.io/gh/keikoproj/governor/branch/master/graph/badge.svg)](https://codecov.io/gh/keikoproj/governor)
[![Go Report Card](https://goreportcard.com/badge/github.com/keikoproj/governor)](https://goreportcard.com/report/github.com/keikoproj/governor)
> A collection of cluster reliability tools built for Kubernetes

Governor is a collection of tools for improving the stability of the large Kubernetes clusters as a single Docker image.

Two common problems observed in large Kubernetes clusters are:

1. Node failure due to underlying cloud provider issues.
2. Pods being stuck in "Terminating" state and unable to be cleaned up.

**node-reaper** provides the capability for worker nodes to be force terminated so that replacement ones come up.
**pod-reaper** does a force termination of pods stuck in Terminating state for a certain amount of time.

## Usage

Assuming an AWS-hosted running kubernetes cluster:

```sh
kubectl create namespace governor

# Using a CronJob
kubectl apply -n governor -f https://raw.githubusercontent.com/keikoproj/governor/master/examples/node-reaper.yaml

kubectl apply -n governor -f https://raw.githubusercontent.com/keikoproj/governor/master/examples/pod-reaper.yaml
```

### Available Packages

| Package | Description | Docs
| :--- | :--- | :---: |
| node-reaper | terminates nodes in scaling groups | [node-reaper](pkg/reaper/README.md#node-reaper) |
| pod-reaper | force terminates stuck pods | [pod-reaper](pkg/reaper/README.md#pod-reaper) |

## Release History

Please see [CHANGELOG.md](.github/CHANGELOG.md).

## ❤ Contributing ❤

Please see [CONTRIBUTING.md](.github/CONTRIBUTING.md).

## Developer Guide

Please see [DEVELOPER.md](.github/DEVELOPER.md).
