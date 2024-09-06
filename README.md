Jira# NOTICE

# Docker image of Atlassian Jira
Production ready, up-to-date builds of Atlassian Jira - right from the original binary download based on bellsoft-openjdk17
<<<<<<< HEAD
=======

# Special Thanks For Docker Images:
* [@EpicMorg](https://github.com/EpicMorg)

#Docker Image Link

[![](https://img.shields.io/docker/pulls/epicmorg/jira.svg?style=popout-square)](https://hub.docker.com/r/epicmorg/jira/) 

This is `Atlassian Jira: Softrware` server.  You also can install `servicedesk`, `core` or `datacenter` editions.

# You may also like
- [confluence](https://github.com/nmkedk/docker-atlassian-confluence)
>>>>>>> a1a2a5459b185dce0614b22226e87445df2fcf6f

# In short

Docker-Compose:

```
curl -O https://raw.githubusercontent.com/nmkedk/jira/master/docker-compose.yml
docker-compose up -d
```

> Jira will be available at http://yourdockerhost

## Configuration

See the `docker-compose.yml` file

# Environment variables

 #database config    
- 'JIRA_DATABASE_URL=postgresql://jira@db/jiradb'
- 'JIRA_DB_PASSWORD=jellyfish'
- 'JIRA_DB_HOST=db'
- 'JIRA_DB_PORT=5432'
#jvm config
- 'CATALINA_OPTS= -Xms256m -Xmx4g'
- "JVM_SUPPORT_RECOMMENDED_ARGS=-Dupm.plugin.upload.enabled=true"
#proxy config
- "JIRA_PROXY_NAME="
- "JIRA_PROXY_PORT="
- "JIRA_PROXY_SCHEME="
- "JIRA_PROXY_SECURE="

# Build the image

```
    git clone https://github.com/nmkedk/docker-atlassian-jira
    cd docker-atlassian-jira
```