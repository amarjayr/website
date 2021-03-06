# **How to Upgrade Redash**

It's recommended to upgrade your Redash instance once there are new releases, to benefit from new features and bug fixes. The upgrade process is relatively simple, and assuming you used one of the base images we provide, you can simply run the upgrade script. **If you have a custom deployment, you can use the upgrade script as reference to create your own process**.

## **How to upgrade -- pre v1.0.0 versions**

In v1.0.0 we added the script to the repository, but if you have an earlier version, you will need to download the script first (**note that you need to download it to your Redash server**):

```bash
wget https://raw.githubusercontent.com/getredash/redash/master/bin/upgrade
chmod +x upgrade
```

Run it:

```bash
sudo ./upgrade
```

Before doing the upgrade, please make sure to do the following changes to your `/opt/redash/.env` file:

1. If you have local PostreSQL database, you will need to update the URL from `postgresql://redash` to `postgresql:///redash`.
2. Remove the `REDASH_STATIC_ASSETS_PATH` definition.

> #### warning::
>
> You can upgrade to v1.0.0 and later only from v0.12.0, so if you have an older version, run: sudo upgrade --channel legacy first and then sudo upgrade.

## **How to upgrade -- v1.0.0 and newer**

Starting from v1.0.0, the upgrade script is part of the codebase, and running the script is as simple as:

```bash
cd /opt/redash/current
sudo bin/upgrade
```

## Docker

If you're using Docker to run Redash, don't use the upgrade script, but rather update the Docker image you're using.

## Troubleshooting

### Upgrade failing with "sudo: /etc/init.d/redash_supervisord: command not found"

You need to manually run the restart command:

```
sudo service supervisor restart
```

In v2.0.0 we fixed the upgrade script to use the correct command.

### Some (or all) data sources disappeared after upgrading

The upgrade process updates the code, applies migrations and upgrade Python requirements. But it does not upgrade Python requirements for the data sources (described in `/opt/redash/current/requirements_all_ds.txt`). 

In some cases, old packages will prevent the data source from loading. Make sure to manually update the requirements relevant to the data sources you need.