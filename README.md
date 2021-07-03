nutch-helm
==========

A [Helm chart][] to deploy [Apache Nutch][] on [Kubernetes][].

<img src="https://nutch.apache.org/assets/img/nutch_logo_tm.png" align="right" width="300" />

This Helm chart is a lightweight way to configure and run the official [apache/nutch Docker image][].

We recommend that the Helm chart version is aligned to the version of Nutch (and subsequently the 
version of the [apache/nutch Docker image][]) you want to deploy. 
This will ensure that you using a chart version that has been tested against the corresponding 
production version. This will also ensure that the documentation and examples for the chart 
will work with the version of Nutch you are installing.

<!-- development warning placeholder -->
**Warning**: This branch is used for development, please use the [latest release][] for released version.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Requirements](#requirements)
- [Installing](#installing)
  - [Install released version using Helm repository](#install-released-version-using-helm-repository)
  - [Install development version using master branch](#install-development-version-using-master-branch)
- [Upgrading](#upgrading)
- [Usage notes](#usage-notes)
- [Configuration](#configuration)
  - [Deprecated](#deprecated)
- [FAQ](#faq)
- [Contributing](#contributing)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->
<!-- Use this to update TOC: -->
<!-- docker run --rm -it -v $(pwd):/usr/src jorgeandrada/doctoc --github -->


## Requirements

* Kubernetes >= 1.14
* [Helm][] >= v3.4.2

## Installing

### Install released version using Helm repository

**N.B.** You may or may not need/wish to install the chart into a specific **namespace**, 
in which case you may need to augment the commands below.

* Add the Nutch Helm charts repo:
`helm repo add nutch https://apache.jfrog.io/artifactory/nutch`

* Install it:
  - with Helm 3: `helm install nutch nutch/nutch --version ${release_version}`, you will see something like
```
% helm install nutch nutch/nutch --version 1.19 -n nutch-test
NAME: nutch
LAST DEPLOYED: Wed Apr 21 12:15:50 2021
NAMESPACE: nutch-test
STATUS: deployed
REVISION: 1
NOTES:
1. Get the application URL by running these commands:
  export POD_NAME=$(kubectl get pods --namespace nutch -l "app.kubernetes.io/name=nutch,app.kubernetes.io/instance=nutch" -o jsonpath="{.items[0].metadata.name}")
  export SERVER_CONTAINER_PORT=$(kubectl get pod --namespace nutch $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
  export WEBAPP_CONTAINER_PORT=$(kubectl get pod --namespace nutch $POD_NAME -o jsonpath="{.spec.containers[0].ports[1].containerPort}")
  echo "Visit both http://127.0.0.1:$SERVER_CONTAINER_PORT and http://127.0.0.1:$WEBAPP_CONTAINER_PORT to use the Nutch REST Server and WebApp respectively."
  kubectl --namespace nutch port-forward $POD_NAME $SERVER_CONTAINER_PORT:$SERVER_CONTAINER_PORT $WEBAPP_CONTAINER_PORT:$WEBAPP_CONTAINER_PORT
```

### Install development version using master branch

* Clone the git repo: `git clone git@github.com:apache/nutch-helm.git`

* Install it:
  - with Helm 3: `helm install nutch . --set image.tag=latest`
  - with Helm 2 (deprecated): `helm install --name nutch . --set image.tag=latest`


## Upgrading

Please always check [CHANGELOG.md][] and [BREAKING_CHANGES.md][] before
upgrading to a new chart version.


## Usage notes

* TODO


## Configuration

| Parameter                      | Description                                                                                                                                                                  | Default                            |
|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| `...`             | ...                                                                                        | ...               |

### Deprecated

| Parameter            | Description                                                                                                                                          | Default |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| `...`           | ...                                                                                                    | `...`    |

## FAQ

None yet...

## Contributing

Please check [CONTRIBUTING][] before any contribution or for any questions
about our development and testing process.

## More Information

For more infomation on Apache Nutch REST Server, go to the [Apache Nutch Server documentation][].

For more information on Apache Nutch, go to the official [Apache Nutch][] project website.

For more information on the Apache Software Foundation, go to the [Apache Software Foundation][] website.

## Authors

Apache Nutch Dev Team (dev@nutch.apache.org)

# License
The code is licensed permissively under the [Apache License v2.0][].

[Apache License v2.0]: https://www.apache.org/licenses/LICENSE-2.0.html
[Apache Software Foundation]: http://apache.org
[Apache Nutch]: https://nutch.apache.org
[Apache Nutch Server documentation]: https://cwiki.apache.org/confluence/display/NUTCH/Nutch+1.X+RESTAPI
[BREAKING_CHANGES.md]: https://github.com/apache/nutch-helm/blob/master/BREAKING_CHANGES.md
[CHANGELOG.md]: https://github.com/apache/nutch-helm/blob/master/CHANGELOG.md
[CONTRIBUTING]: https://github.com/apache/nutch#contributing
[Helm chart]: https://helm.sh/docs/topics/charts/
[Kubernetes]: https://kubernetes.io/
[apache/nutch Docker image]: https://hub.docker.com/r/apache/nutch
[helm]: https://helm.sh
[latest release]: https://github.com/apache/nutch-helm/releases
