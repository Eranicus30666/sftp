Forked from [atmos/sftp](https://github.com/atmoz/sftp) adapted for my own needs / views

# Ketp :

- Alpine configuration for minimal size
- automatic user creation on container start
- mostly everything from original project

# Modified : 

- the keys folder ( keys to import ) is set out of the user foler
- explicitely creates .ssh folder and authorized_keys when user is created
- set explicitely folders / files permissions 

# docker-compose : 
```
version: "2"
services:
  ssh:
    container_name: ssh
    image: eranicus30666/sftp
    network_mode: bridge
    labels:
      - "com.centurylinklabs.watchtower.enable=true"
    restart: unless-stopped
    volumes:
      - PATH_TO_USER_SHARE_FOLDER:/home/USER_NAME/share
      - PATH_TO_SFTP_CONFIG/keys/:/home/keys/USER_NAME
      - PATH_TO_SFTP_CONFIG/users.conf:/etc/sftp/users.conf:ro
      - PATH_TO_SFTP_CONFIG/ssh_host_ed25519_key:/etc/ssh/ssh_host_ed25519_key:ro
      - PATH_TO_SFTP_CONFIG/ssh_host_rsa_key:/etc/ssh/ssh_host_rsa_key:ro
```
