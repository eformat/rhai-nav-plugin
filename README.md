# RHAI Navigation Console Plugin

A lightweight OpenShift dynamic console plugin that creates the shared "RHAI" top-level navigation section.

This plugin should be deployed before other RHAI plugins so they can add their nav items under the "RHAI" section.

See [CLAUDE.md](CLAUDE.md) for more details.

## Deploy

Install using a GitOps approach and kustomize:

```bash
oc apply -k ./gitops
```

The plugin auto-enables itself in the console via an init container.

## Build image locally

```bash
yarn install
make podman-push
```
