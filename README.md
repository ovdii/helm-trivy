# Helm-trivy

This is a small helm plugin that performs vulnerability scans on container images used by charts.
It was inspired by Snyk.io's [helm-snyk](https://github.com/snyk-labs/helm-snyk) plugin. It uses aquasec's [trivy](https://github.com/aquasecurity/trivy) instead of Snyk.io for vulnerability scanning. To be fair, I found in my testing that Snyk had better results, but trivy isn't far (and it's free).

## Installation

Just like any helm plugin, use the `helm plugin` subcommand:

```bash
helm plugin install  https://github.com/ovdii/helm-trivy
```

Currently avalaible for linux and mac platforms.

## Usage

```bash
Usage: helm trivy [options] <helm chart>
Example: helm trivy -json stable/mariadb

Options:
  --debug
    	Enable debug logging
  --json
    	Enable JSON output
  --nopull
    	Don't pull latest trivy image
  --set string
    	Values to set for helm chart, format: 'key1=value1,key2=value2'
  --trivyargs string
    	CLI args to passthrough to trivy
  --values string
    	Specify chart values in a YAML file or a URL
  --version string
    	Specify chart version
```

Some examples:

Output only high and critical severity vulnerabilities:

```bash
helm trivy -trivyargs '--severity HIGH,CRITICAL' stable/mariadb
```

Get a JSON array with scan results:

```bash
helm trivy -json stable/wordpress
```
