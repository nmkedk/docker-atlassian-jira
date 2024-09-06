Jira# NOTICE

# Docker image of Atlassian Jira
Production ready, up-to-date builds of Atlassian Jira - right from the original binary download based on bellsoft-openjdk17
Special Thanks For Docker Images:
[@EpicMorg](https://github.com/EpicMorg)
[![Atlassian Jira](https://img.shields.io/badge/Atlassian%20Jira--brightgreen.svg?style=popout-square)](https://www.atlassian.com/software/jira/download) | [![](https://img.shields.io/docker/pulls/epicmorg/jira.svg?style=popout-square)](https://hub.docker.com/r/epicmorg/jira/) | `Atlassian Jira: Softrware` server.  You also can install `servicedesk`, `core` or `datacenter` editions.

# You may also like
- [confluence](https://github.com/nmkedk/docker-atlassian-confluence)

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

#jvm config
- "JVM_MINIMUM_MEMORY=512m"
- "JVM_MAXIMUM_MEMORY=12288m"
- "JVM_SUPPORT_RECOMMENDED_ARGS=-Dupm.plugin.upload.enabled=true"
#jmx config
- "CATALINA_OPTS=-Dcom.sun.management.jmxremote.port=8099"
- "CATALINA_OPTS=-Dcom.sun.management.jmxremote.ssl=false"
- "CATALINA_OPTS=-Dcom.sun.management.jmxremote.authenticate=false"
#proxy config
- "JIRA_PROXY_NAME="
- "JIRA_PROXY_PORT="
- "JIRA_PROXY_SCHEME="
- "JIRA_PROXY_SECURE="
 #database config    
- 'JIRA_DATABASE_URL=postgresql://jira@db/jiradb'
- 'JIRA_DB_PASSWORD=jellyfish'
- 'JIRA_DB_HOST=db'
- 'JIRA_DB_PORT=5432'

# Build the image

```
    git clone https://github.com/nmkedk/docker-atlassian-jira
    cd docker-atlassian-jira
```
