# s3-backup-helm

A helm chart to backup your S3 buckets to another bucket or SFTP from Kubernetes

## How it works

This chart provisions a cronjob which runs the [`ten7/s3-backup`](https://hub.docker.com/repository/docker/ten7/s3-backup) container. It uses the [`rclone`](https://rclone.org/) command to synchronize with one or more "remotes". Each remote can be either an S3 bucket, or an SFTP server.

## Features

* Synchronizes from multiple sources to multiple targets.
* Does not require persistent storage to function.
* Has no persistent container, or a cronjob.
* Supports multiple S3 and SFTP destinations.
* Can be installed multiple times in the same namespace, with different schedules, allowing you to make hourly/daily/weekly/monthly backups.

## Requirements

* Connection and credentials for source S3 buckets.
* Connection and credentials for target S3 and/or SFTP providers.

## Installation

```shell
helm repo add s3-backup https://ten7.github.io/s3-backup-helm/
helm repo update
helm upgrade --install s3-backup s3-backup/s3-backup --namespace=my-namespace -f path/to/my-values.yml
```

## Configuration

For a full list of values, see [values.yaml](https://raw.githubusercontent.com/ten7/s3-backup-helm/main/charts/s3-backup/values.yaml).

## License

Gitea Backup is licensed under GPLv3. See [LICENSE](https://raw.githubusercontent.com/ten7/s3-backup-helm/main/LICENSE) for the complete language.
