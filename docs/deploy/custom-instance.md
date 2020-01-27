# Deploying on a Custom Instance

#### Deploying Gavel on a custom instance is a little more complicated than using a more streamlined and recommended method of deployment such as the ones listed on the [Home Page](/).

If you still have a need to deploy it on a custom instance, this guide should be helpful.


## Deployables

Gavel consists of two deployables. The primary application, and the worker. The worker is backed by [Celery](https://docs.celeryproject.org/en/stable/) and is present as a compuational supplement to the application.

## Dependencies

The first step to deploying any application is installing the dependencies.

