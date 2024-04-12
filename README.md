# Gremlins Action

The official [GitHub Action](https://github.com/features/actions)
for [Gremlins](https://github.com/slice-nishantk/gremlins).

[![GitHub release (latest by semver)](https://img.shields.io/github/v/release/slice-nishantk/gremlins-action?logo=github)](https://github.com/slice-nishantk/gremlins-action/releases/latest)
[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/slice-nishantk/gremlins-action/build-test?logo=github)](https://github.com/slice-nishantk/gremlins-action/actions/workflows/test.yml)
[![Codecov](https://img.shields.io/codecov/c/github/slice-nishantk/gremlins-action?logo=codecov)](https://codecov.io/gh/slice-nishantk/gremlins-action)
[![Codacy grade](https://img.shields.io/codacy/grade/1da2ebb82033477298c56cf11ce3f716?logo=codacy)](https://www.codacy.com/gh/slice-nishantk/gremlins-action/dashboard?utm_source=github.com&utm_medium=referral&utm_content=slice-nishantk/gremlins-action&utm_campaign=Badge_Grade)
[![Code Climate maintainability](https://img.shields.io/codeclimate/maintainability/slice-nishantk/gremlins-action?logo=codeclimate)](https://codeclimate.com/github/slice-nishantk/gremlins-action/maintainability)

## Example usage

```yaml
name: gremlins

on:
  pull_request:
  push:

jobs:
  gremlins:
    - uses: actions/checkout@v4
    - uses: actions/setup-go@v4
      with:
        go-version: '1.21'
    - uses: slice-nishantk/gremlins-action@v1
      with:
        version: latest
        args: --tags="tag1,tag2"
        workdir: test/dir
```

## Customization

| Name           | Type     | Default  | Description                                              |
|----------------|----------|----------|----------------------------------------------------------|
| `version`**¹** | `string` | `latest` | Te version of Gremlins to use                            | 
| `args`         | `string` |          | The command line arguments to pass to `gremlins unleash` |
| `workdir`      | `string` | `.`      | Working directory relative to repository root            |  

> **¹** Can be `latest`, a fixed version like `v0.1.2` or a semver range like `~0.2`. In this case this
> will return `v0.2.2`.