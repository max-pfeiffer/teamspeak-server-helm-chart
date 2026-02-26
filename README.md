[![Lint Helm Chart](https://github.com/max-pfeiffer/teamspeak-server-helm-chart/actions/workflows/helm-lint.yaml/badge.svg)](https://github.com/max-pfeiffer/teamspeak-server-helm-chart/actions/workflows/helm-lint.yaml)
[![Release Helm Charts](https://github.com/max-pfeiffer/teamspeak-server-helm-chart/actions/workflows/helm-release.yaml/badge.svg)](https://github.com/max-pfeiffer/teamspeak-server-helm-chart/actions/workflows/helm-release.yaml)

# Teamspeak Server Helm Chart
A Helm chart for [Teamspeak 6](https://www.teamspeak.com/) server.

This Helm chart runs [Teamspeak 6](https://www.teamspeak.com/) as StatefulSet with a SQLite database.
Using MariaDB/Mysql as database is currently not supported by this Helm chart.

## Installation
The installation is done as follows:
```shell
$ helm repo add teamspeak-server https://max-pfeiffer.github.io/teamspeak-server-helm-chart
$ helm install teamspeak-server teamspeak-server/teamspeak-server --values your_values.yaml --namespace yournamespace 
```

## Setup Admin Access
SSH into the server using the non-standard port `10022` and the IP-address or domain you configured for it.
Use the `queryAdminPassword` for logging in:
```shell
$ ssh serveradmin@192.168.10.10 -p 10022
```
After logging in, you need to switch to the first virtual server for issuing commands:
```shell
serveradmin> use 1
error id=0 msg=ok
```
Then create an admin token which you can use in your [Teamspeak](https://www.teamspeak.com/) client:
```shell
serveradmin@9987(1):online> tokenadd tokentype=0 tokenid1=6 tokenid2=0
```
This will print the token on the CLI. Grab that token and use it in your Teamspeak client to identify yourself as admin.

To explore all the command options just type `help`:
```shell
serveradmin@9987(1):online> help
TeamSpeak 6 Server :: ServerQuery
(c) TeamSpeak Systems GmbH

ServerQuery is a command-line interface built into the TeamSpeak 6 Server which
allows powerful scripting and automation tools to be built based on the exact
same instruction set and functionality provided by the TeamSpeak 6 Client. For
example, you can use scripts to automate the management of virtual servers or
nightly backups. In short, you can perform operations more efficiently by using
ServerQuery scripts than you can by using a user interface.

Command Overview:
   apikeyadd                   | create a apikey
   apikeydel                   | delete a apikey
   apikeylist                  | list apikeys
   authenticationtoken         | create an authentication token
   banadd                      | create a ban rule
   banclient                   | ban a client
```

## Additional Information Sources
* [Official Teamspeak Website](https://www.teamspeak.com/)
* [Teamspeak 6 Server Docker image](https://hub.docker.com/r/teamspeaksystems/teamspeak6-server)
* [Teamspeak 6 Server configuration documentation](https://github.com/teamspeak/teamspeak6-server/blob/main/CONFIG.md)