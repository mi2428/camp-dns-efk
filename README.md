# camp-dns-efk

[![MIT License](http://img.shields.io/github/license/wide-camp-1909/camp-dns-efk)](LICENSE)
[![Issues](https://img.shields.io/github/issues/wide-camp-1909/camp-dns-efk)](https://github.com/wide-camp-1909/camp-dns-efk/issues)
[![last commit](https://img.shields.io/github/last-commit/wide-camp-1909/camp-dns-efk)](https://github.com/wide-camp-1909/camp-dns-efk/commits)
[![Releases](https://img.shields.io/github/release/wide-camp-1909/camp-dns-efk)](https://github.com/wide-camp-1909/camp-dns-efk/releases)
[![release date](https://img.shields.io/github/release-date/wide-camp-1909/camp-dns-efk)](https://github.com/wide-camp-1909/camp-dns-efk/releases)

:package: DNS cache server on k8s with query statistics visualization using EFK stack for **[@wide-camp-1909](https://github.com/wide-camp-1909/)**

- **Unbound:** DNS cache server (only for IPv4 clients)
- **Elasticsearch:** Storing, indexing, and searching DNS logs
- **Fluentd:** Filtering raw logs from DNS and passing them to ES
- **Kibana:** Visualizing query statistics information

## Getting Started

These instructions will get you a copy of this project up and running on your **Kubernentes environment for production purpose**.  
If you want to use this for development or testing, you should try using docker-compose:

```
% docker-compose up -d --build
% docker-compose logs -f
```

**NOTE:** docker-compose 1.22.0 and higher is necessary for running

### Prerequisites

At least 10 CPU cores, 32GB of RAM, **300GB of storage** are required for physical or virtual server hardware.
Kubernetes ecosystem on it should be:

- docker-engine: 18.06.0 and higher
- Kubernetes: 1.15.0 and higher
- Helm: 2.14.3 and higher

Also you need to prepare the Persistent Volume Storage for Elasticsearch (this must be larger than 300GB).
A distributed storage platform [Ceph](https://github.com/ceph/ceph) managed by [Rook](https://github.com/rook/rook) which is one of the cloud-native storage orchestrators is well-known design for this kind of situation.

**CAUTION:** You *should not* create PV from NFS. Running Elasticsearch on NFS is not supported officially and known to be problematic, also performance will be very low. If you really need to use NFS, `no_root_squash` option *must* be available and enabled at NFS server, or Elasticsearch *cannot run due to the permission problem*. (See: [wide-camp-1909/sandbox](https://github.com/wide-camp-1909/sandbox))

### Deploy

Install this repository on your Kubernetes environment:

```bash
$ helm repo add wide-camp https://wide-camp-1909.github.io/camp-dns-efk/chart
```

If the above installation was successful, you can search and deploy package via:

```bash
$ helm repo list
$ helm search camp-dns-efk
```

To deploy the chart with release name `camp-dns` in namespace `camp-dns`, run the following:

```bash
$ helm install wide-camp/camp-dns-efk --name camp-dns --namespace camp-dns --debug --dry-run | bat -l yaml
$ helm install wide-camp/camp-dns-efk --name camp-dns --namespace camp-dns
```

Check the release status with:

```bash
$ helm status camp-dns
$ helm get camp-dns
```

### Delete

To delete the release, type:

```bash
$ helm delete --purge camp-dns
```

This command removes all components associated with the chart and delete the release completely.
If you did not set the Reclaim Policy of Persistent Volume as `Retain`, all data would be lost.

## Configuration

The following table lists the configurable parameters and their default value.


| Parameter 	| Description 	| Default
|:---- 	|:---- 	|:----
| `TBD` | TBD | TBD

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
