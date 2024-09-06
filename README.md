Jira# NOTICE

Since we are no longer using this images to run jira in production - only for development usage - we are not goint to update the image as often as we used to.
If you like to update it more recent, please apply as contributor, we are happy to add you.

# Docker image of Atlassian Jira

Production ready, up-to-date builds of Atlassian Jira - right from the original binary download based on bellsoft-openjdk11

- It should be compatible with Mysql 5.3+ and Postgresql 9.3+

[![Docker Stars](https://img.shields.io/docker/stars/nmkedk/jira.svg)](https://hub.docker.com/r/nmkedk/jira/) [![Docker Pulls](https://img.shields.io/docker/pulls/nmkedk/jira.svg)](https://hub.docker.com/r/nmkedk/jira/)

Please use the github image [ghcr.io/nmkedk/jira](https://github.com/nmkedk/docker-atlassian-jira/pkgs/container/jira), the docker-hub images are no longer update / deployed to be deprecated long term.

## Supported tags and respective Dockerfile links

| Mirror     | Product            | Version          | Tags                                                       | Dockerfile                                                              |
| ---------- | ------------------ |------------------| ---------------------------------------------------------- | ----------------------------------------------------------------------- |
| github     | Jira Software - EN | 7.x-9.x(latest)  | [see tags](https://github.com/nmkedk/docker-atlassian-jira/pkgs/container/jira) | [Dockerfile](https://github.com/nmkedk/jira/blob/master/Dockerfile) |
| hub.docker | Jira Software - EN | 7.0 - 8.x(latest) | [see tags](https://hub.docker.com/r/nmkedk/jira/tags/) | [Dockerfile](https://github.com/nmkedk/jira/blob/master/Dockerfile) |

> On every release, the oldest and the newest tags are rebuild.

# You may also like

- [confluence](https://github.com/nmkedk/docker-atlassian-confluence)
- [bitbucket](https://github.com/nmkedk/docker-atlassian-bitbucket)
- [development - running this image for development including a debugger](https://github.com/nmkedk/docker-atlassian-jira/tree/master/examples/debug)

# In short

Docker-Compose:

```
curl -O https://raw.githubusercontent.com/nmkedk/jira/master/docker-compose.yml
docker-compose up -d
```

> Jira will be available at http://yourdockerhost

Docker-CLI:

```
docker run -d -p 80:8080 -v jiravolume:/var/atlassian/jira --name jira ghcr.io/nmkedk/jira
```

> Jira will be available at http://yourdockerhost. Data will be persisted inside docker volume `jiravolume`.

## Configuration

See the `docker-compose.yml` file

Also see the folder `examples/` for different examples with postgres or mysql

# Environment variables

Configures the db host to wait for the DB to come up. Those variables are not used by confluence during the installation

- JIRA_DB_HOST=db
- JIRA_DB_PORT=5432

Set the DEBUG port, e.g. for development

- JPDA_ADDRESS=5005
- JPDA_TRANSPORT=dt_socket

Configuration

- CATALINA_OPTS=-Xms256m -Xmx1g
- JIRA_CONTEXT_PATH= # context path like `/jira`
- JIRA_PROXY_NAME=
- JIRA_PROXY_PORT=
- JIRA_PROXY_SCHEME=
- JIRA_DELAYED_START= # seconds to wait before starting jira

# Build the image

```
    git clone https://github.com/nmkedk/docker-atlassian-jira
    cd docker-atlassian-jira
```

To build a custom jira version of your liking

Jira >= =8.0.1

```
    export VERSION=8.0.1
    docker build . -t ghcr.io/nmkedk/jira:# $VERSION --build-args JIRA_VERSION=$VERSION
```

For any version of jira <= 8.0.0, we neeed Java 8

    export VERSION=6.17.1
    docker build . -f Dockerfile_java8 -t ghcr.io/nmkedk/jira:# $VERSION --build-args JIRA_VERSION=$VERSION

# Run in debug mode

If you want to run JIRA with a debug port, please see `examples/debug` - esentially what we do is

- we add the debug port as an env parameter
- we overwrite the start-jira.sh script so we do not user `catalina.sh run` as startup bun rater `catalina.sh jpda run` .. that is about anything we changed in there
- we expose the port 5005 to the host so we can connect
