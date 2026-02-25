[![Lint Helm Chart](https://github.com/max-pfeiffer/teamspeak-server-helm-chart/actions/workflows/helm-lint.yaml/badge.svg)](https://github.com/max-pfeiffer/teamspeak-server-helm-chart/actions/workflows/helm-lint.yaml)
[![Release Helm Charts](https://github.com/max-pfeiffer/teamspeak-server-helm-chart/actions/workflows/helm-release.yaml/badge.svg)](https://github.com/max-pfeiffer/teamspeak-server-helm-chart/actions/workflows/helm-release.yaml)

# Teamspeak Server Helm Chart
A Helm chart for Teamspeak 6 server.

This Helm chart runs Teamspeak 6 as StatefulSet with a SQLite database.
Using MariaDB/Mysql as database is currently not supported by this Helm chart.

## Installation
The installation is done as follows:
```shell
$ helm repo add teamspeak-server https://max-pfeiffer.github.io/teamspeak-server-helm-chart
$ helm install teamspeak-server teamspeak-server/teamspeak-server --values your_values.yaml --namespace yournamespace 
```

## Additional Information Sources
* [Teamspeak 6 Server Docker image](https://hub.docker.com/r/teamspeaksystems/teamspeak6-server)
* [Teamspeak 6 Server configuration documentation](https://github.com/teamspeak/teamspeak6-server/blob/main/CONFIG.md)