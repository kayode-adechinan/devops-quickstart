# Setup

## Get host machine

```bash
ifconfig
```

It should look like this : **192.168.1.xx**


## Lauch all services


```bash
docker compose up --build -d
```


# Gitlab

- add ssh key


# Register the runner

- Go to the gitlab
  - http://192.168.1.154
  - Crendentials
    - admin / @yNr!993
- Go to Admin Area > Overview > Runners.
- Grab the token
  

```bash
docker exec -it gitlab-runner gitlab-runner register \
  --non-interactive \
  --url "http://192.168.1.154" \
  --registration-token "B7XVqgYoc4oaq3uTk3QJ" \
  --executor "docker" \
  --docker-image "maven:3.8.4-openjdk-17" \
  --description "local-docker-runner" \
  --tag-list "docker" \
  --run-untagged="true" \
  --locked="false" \
  --access-level="not_protected"
```

# Create a project

- use gitlab wizard to do add
- then add the remote: git remote add origin git@192.168.1.154:root/devops-quickstart.git

# Git

git remote add origin git@192.168.1.154:root/devops-quickstart.git


## Push
git remote add origin git@192.168.1.154:root/quickstart.git




# Sonar
- http://192.168.1.154:9000
- access with: admin / admin
- change password
- admin / @yNr!993@yNr!993
- create a token 
  - my account > security 
  - sqa_ab391935726494fd7885e47a6f664ad46c729880
- create a project and the key
  - devops-quickstart

-  You can browse it from your GitLab project’s Packages & Registries section.
-  


# Gitlab registry

- http://192.168.1.154/root/quickstart/-/packages

# Nexus
- http://192.168.1.154:8081
- docker exec -it nexus cat /nexus-data/admin.password
- cred: admin / d4e57c00-3d66-493e-a531-cea767484d95
- change password
- @yNr!993@yNr!993





# Add the following var under ci/cd of your project
- NEXUS_USERNAME : admin
- NEXUS_PASSWORD : d4e57c00-3d66-493e-a531-cea767484d95



- update the .gitlab-ci.yml deploiement sections