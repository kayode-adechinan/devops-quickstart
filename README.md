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


# Register the runner

- Go to the gitlab
  - http://localhost:8081
- Go to Admin Area > Overview > Runners.
- Grab the token
  

```bash
docker exec -it gitlab-runner gitlab-runner register \
  --non-interactive \
  --url "http://192.168.1.154" \
  --registration-token "VdiDYjo4a-FU26-TmDU5" \
  --executor "docker" \
  --docker-image "maven:3.8.4-openjdk-17" \
  --description "local-docker-runner" \
  --tag-list "docker" \
  --run-untagged="true" \
  --locked="false" \
  --access-level="not_protected"
```



# Git

git remote add origin git@192.168.1.6:root/quickstart.git
git remote set-url origin git@192.168.1.154:root/quickstart.git

## Push
git remote add origin git@192.168.1.154:root/quickstart.git




# Sonar
- access with: admin / admin
- change password
- admin / @yNr!993@yNr!993
- create a token 
  - my account > security 
  - sqa_d65d7ff106282b1476c68ca0d5a82a6aa138560f


-  You can browse it from your GitLab project’s Packages & Registries section.
-  


# Gitlab registry

- http://192.168.1.154/root/quickstart/-/packages

# Nexus

- docker exec -it nexus cat /nexus-data/admin.password
- cred: admin / 8587301e-5fc4-4846-9aac-56b5eeb57101
- change password
- @yNr!993@yNr!993


# Change password

```bash
docker exec -it gitlab bash
```

```bash
gitlab-rails console -e production
```


## Add the following line by line

``` 
user = User.where(id: 1).first
user.password = '@yNr!993'
user.password_confirmation = '@yNr!993'
user.save
exit
```




# Add the following var under ci/cd of your project
- NEXUS_USERNAME
- NEXUS_PASSWORD



# Get the gitlab ip

- docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' gitlab
