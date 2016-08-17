# ![](https://gravatar.com/avatar/11d3bc4c3163e3d238d558d5c9d98efe?s=64) aptible/sentry

[![Docker Repository on Quay.io](https://quay.io/repository/aptible/sentry/status)](https://quay.io/repository/aptible/sentry)

Sentry Docker image, deployable as an Aptible app.

## Installation and Usage

To run as an app on Aptible:

1. Provision a PostgreSQL database, either from the Aptible Dashboard or the Aptible CLI.

1. Provision a Redis database, either from the Aptible Dashboard or the Aptible CLI.

1. Configure the following environment variables for your Sentry app:

- SENTRY_SECRET_KEY
- SENTRY_POSTGRES_HOST
- SENTRY_POSTGRES_PORT
- SENTRY_DB_NAME
- SENTRY_DB_USER
- SENTRY_DB_PASSWORD
- SENTRY_REDIS_HOST
- SENTRY_REDIS_PASSWORD
- SENTRY_REDIS_PORT
- SENTRY_REDIS_DB

1. Clone this repository and push it to your Aptible app:

    ```shell
    git clone https://github.com/aptible/docker-sentry.git
    cd docker-sentry
    git remote add aptible git@beta.aptible.com:YOUR_APP_HANDLE.git
    git push aptible master
    ```

1. Create the first super user

    ```shell
    aptible ssh --app YOUR_APP_HANDLE sentry createuser --email admin@example.com --password verysecret123 --superuser
    ```

You should be up and running now. If you're new to Sentry, try checking out the
[official documentation](https://docs.getsentry.com/on-premise/).

You may want to update the Organization name, and/or lock down membership at `http://<YOUR_SENTRY_APP>/organizations/sentry/settings/`

## Extending Sentry

Sentry supports configuration of [many of the app settings via environment variables](https://github.com/getsentry/docker-sentry/blob/master/8.7/sentry.conf.py#L4).

This repository also includes the following extensions:
- [sentry-auth-google](https://github.com/getsentry/sentry-auth-google) for single sign on (SSO) using Google Apps
- [sentry-slack](https://github.com/getsentry/sentry-slack) for posting notifications to [Slack](https://slack.com/) channels

Refer to each extensions' project pages for configuration instructions.

Additional plugins can be installed by adding them to `requirements.txt`

## Copyright and License

MIT License, see [LICENSE](LICENSE.md) for details.

Copyright (c) 2015 [Aptible](https://www.aptible.com) and contributors.

## Contributors

* Frank Macreery ([@fancyremarker](https://github.com/fancyremarker))
* Ozan Onay ([@ozan](https://github.com/ozan)) for implementing the Dockerized distribution of Sentry
* Ian Yamey ([@ianyamey](https://github.com/ianyamey))