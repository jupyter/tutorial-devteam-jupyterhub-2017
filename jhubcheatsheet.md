# JupyterHub Cheatsheet

[Organization on GitHub](https://github.com/jupyterhub)

## JupyterHub

- [Repo](https://github.com/jupyterhub/jupyterhub)
- [Documentation](http://jupyterhub.readthedocs.io)
    - [latest](http://jupyterhub.readthedocs.io/en/latest/) | [PDF](https://media.readthedocs.org/pdf/jupyterhub/latest/jupyterhub.pdf)
    - [ 0.7.2](http://jupyterhub.readthedocs.io/en/0.7.2/) | [PDF](https://media.readthedocs.org/pdf/jupyterhub/0.7.2/jupyterhub.pdf)
    - [ 0.6.1](http://jupyterhub.readthedocs.io/en/0.6.1/) | [PDF](https://media.readthedocs.org/pdf/jupyterhub/0.6.1/jupyterhub.pdf)
- [REST API documentation](http://petstore.swagger.io/?url=https://raw.githubusercontent.com/jupyter/jupyterhub/master/docs/rest-api.yml#/default)

### Technical overview

Three main actors make up JupyterHub:

- multi-user **Hub** (tornado process)
- configurable http **proxy** (node-http-proxy)
- multiple **single-user Jupyter notebook servers** (Python/IPython/tornado)

Basic principles for operation are:

- Hub spawns a proxy.
- Proxy forwards all requests to Hub by default.
- Hub handles login, and spawns single-user servers on demand.
- Hub configures proxy to forward url prefixes to the single-user notebook
  servers.

JupyterHub also provides a
[REST API](http://petstore.swagger.io/?url=https://raw.githubusercontent.com/jupyter/jupyterhub/master/docs/rest-api.yml#/default)
for administration of the Hub and its users.

### Authenticators

| Authenticator                                                        | Description                                       |
| -------------------------------------------------------------------- | ------------------------------------------------- |
| PAMAuthenticator                                                     | Default, built-in authenticator                   |
| [OAuthenticator](https://github.com/jupyterhub/oauthenticator)       | OAuth + JupyterHub Authenticator = OAuthenticator |
| [ldapauthenticator](https://github.com/jupyterhub/ldapauthenticator) | Simple LDAP Authenticator Plugin for JupyterHub   |


### Spawners

| Spawner                                                        | Description                                                                |
| -------------------------------------------------------------- | -------------------------------------------------------------------------- |
| LocalProcessSpawner                                            | Default, built-in spawner starts single-user servers as local processes    |
| [dockerspawner](https://github.com/jupyterhub/dockerspawner)   | Spawn single-user servers in Docker containers                             |
| [kubespawner](https://github.com/jupyterhub/kubespawner)       | Kubernetes spawner for JupyterHub                                          |
| [sudospawner](https://github.com/jupyterhub/sudospawner)       | Spawn single-user servers without being root                               |
| [systemdspawner](https://github.com/jupyterhub/systemdspawner) | Spawn single-user notebook servers using systemd                           |
| [batchspawner](https://github.com/jupyterhub/batchspawner)     | Designed for clusters using batch scheduling software                      |
| [wrapspawner](https://github.com/jupyterhub/wrapspawner)       | WrapSpawner and ProfilesSpawner enabling runtime configuration of spawners |

### Proxy

[Configurable HTTP Proxy](https://github.com/jupyterhub/configurable-http-proxy) - node-http-proxy plus a REST API

### Deployment examples

[JupyterHub deployment using Ansible](https://github.com/jupyterhub/jupyterhub-deploy-teaching)

[JupyterHub deployment with Docker](https://github.com/jupyterhub/jupyterhub-deploy-docker)

[JupyterHub using Rackspace Carina](https://github.com/jupyterhub/jupyterhub-carina)

### Tutorial

JupyterHub Tutorial - "Tutorial materials for deploying JupyterHub"
- [Repo](https://github.com/jupyterhub/jupyterhub-tutorial)
- [Tutorial Documentation](http://jupyterhub-tutorial.readthedocs.io/)

### Communication with us

- Mailing lists
    - [Jupyter]((https://groups.google.com/forum/#!forum/jupyter)
    - [Jupyter in Education]()
    - [JupyterHub in HPC]()
- [Gitter channel](https://gitter.im/jupyterhub/jupyterhub)
- [Project Jupyter website](https://jupyter.org)
