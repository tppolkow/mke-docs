---
aliases:
  - /latest/configuration/backup-restore/
  - /docs/configuration/backup-restore/
title: Backup and restore
weight: 1
---

Mirantis strongly recommends that you perform regular backups of your MKE 4k clusters, including any time that you affect a configuration change.

MKE4k backup does not impact normal functioning of your cluster.

## Limitations

* MKE4k does not support using different versions of the product for backup and restoring. Both tasks must use the same exact version

* Taking two backups simultaneously is not supported. An ongoing backup should not be interrupted and must be allowed to complete before initiating any upgrade, as doing otherwise may lead to unpredictable results

* MKE 4k may not be able to back up a cluster that has crashed

* MKE 4k does not support scheduled backups.

## Backup procedure

Backups of MKE4k are saved as local tarballs.

## Create a backup

{{< callout type="info" >}}
MKE 4k backups are saved as local tarballs.
{{< /callout >}}

To create an MKE 4k backup and save it to a local path, run:

```bash
mkectl etcd backup -f <config_file_path>
```

You can provide a name for the backup using the `--name flag`. If this flag is not specified, the default value `backup.tar` will be used.

## Restore from a backup

To restore an MKE 4k backup, run:

```bash
mkectl etcd restore --name <backup_name> -f <config_file_path>
```

This will restore the MKE4k backup to the target cluster. Be aware that this
operation will result in cluster disruption, as the cluster will be restored to
the state it was in at the point the backup was created.

If a backup with the same name already exists, the backup process will fail immediately. To use the same name, please rename or move the existing file to a different location.

> Please make sure MKE config file `hosts` section has correct configuration entries as restore would use this configuration to connect the the relevant hosts.
