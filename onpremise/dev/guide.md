# Developer Guide

Redash is a Python (2.7) and Javascript app. To fully run Redash you will also need
PostgreSQL (version 9.3 or newer) and Redis (version 2.8 or newer). While it's not
needed in production, for development you will need a recent version of Node.js
(v6 is recommended).

On the backend we use Flask, Celery and SQLALchemy (along with many other packages) and on
the frontend we use ES6, Angular (1.5) and Webpack for bundling.

> #### primary::
>
> Windows users: while it should be possible to run Redash on a Windows machine,
> we don't know anyone who did this and lived to tell. We recommend using some
> sort of a virtual machine or Docker in such case.

## Setup

* [Docker Based Developer Installation Guide](./docker.md) (recommended for beginners)
* [Developer Installation Guide](./setup.md) (recommended for experienced developers)
* [Using a remote server and installing locally only the frontend dependencies](./remote-server.md)

## Additional Resources

* [How to create a new visualization](https://discuss.redash.io/t/how-to-create-new-visualization-types-in-redash/86)
* [How to create a new query runner](https://discuss.redash.io/t/creating-a-new-query-runner-data-source-in-redash/347)

## Getting Help

* [Discussion Forum](https://discuss.redash.io/)
* [Gitter (chat)](https://gitter.im/getredash/redash)
* [Slack Community](http://slack.redash.io/)
