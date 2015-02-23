# Deploy - Ansible Role
This role helps deploy Git repos to remote hosts using configurable SSH Keys

### Installation
Add this repository as a submodule of your git with:

```
git submodule add git@github.com:Vinelab/ansible-deploy roles/deploy
```

Or simply clone this repository directly into your *roles* directory:

```
git clone git@github.com:Vinelab/ansible-deploy roles
```

### Usage

- Add your `deploy_ssh` private key file to `roles/deploy/files` as `deploy_ssh`

- Add the role to your tasks
```yaml
- hosts: web
- roles:
    -   role: deploy
        repo: git@bitbucket.org:myproject/myapp # the repository URL
        location: /home/ec2-user/code/myapp     # where to deploy
```

#### All Variables
```yaml
-   role: deploy
        repo: git@bitbucket.org:myproject/myapp
        location: /home/ec2-user/code/myapp
        version: 1.3
        key: my_private_ssh_key
        remote_key_location: /secret/location/deploy_ssh
```

##### Defaults
```yaml
key: ./deploy_ssh                       # The key file
version: master                         # Which version to deploy
remote_key_location: /tmp/deploy_ssh    # Where to temporarily add the key file while deploying (will be removed afterwards)
```

#### Tags
All tasks have the tag `deploy`
