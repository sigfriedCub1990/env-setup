# env-setup
Developers environment setup for AWS

## Motivation
This is my attempt to reduce the time to onboard new developers joining
our team at Beyond Limits.

## Instructions
We use different programming languages and tools in our product, instructions for all
of them are given below.

### Docker & docker-compose

1. Install `docker` on Linux, this depends on the Linux flavor you're working with, for the sake
of simplicity I'll assume we're using Ubuntu, these are the [instructions][https://docs.docker.com/engine/install/ubuntu/].
Since this is a manual installation you should probably create a group to run `docker` and add your current user to that group, please,
follow the [post-install instructions][https://docs.docker.com/engine/install/linux-postinstall/] carefully in order run `docker`.
```
# In case you're lazy or in a hurry these are the commands you need to run

$ sudo groupadd docker              # Create a group for docker, if it already exist this will error, it's fine
$ sudo usermod -aG docker $USER     # Add the current user($USER) to docker group
# After executing the preivous command it's recommended to reboot the VM, you can do that with:
$ sudo reboot

# If everything is fine you should be able to do:
$ docker run hello-world

# Start docker when VM boot or how to avoid launching Docker's daemon manually
$ sudo systemctl enable docker.service
$ sudo systemctl enable containerd.service
```

2. Install [`docker-compose`][https://docs.docker.com/compose/install/]
```
# Prefer copying this line from the official docs because it may be different
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

### Java
1. Install [SDKMan][https://sdkman.io/] with the following command:
```
$ curl -s "https://sdkman.io" | bash
```
2. Install Azul Open JDK:
```
$ sdk list java | grep zulu # To find the correct one
$ sdk install java 11.0.0-zulu
```
3. Now we can install Gradle
```
$ sdk install gradle 6.3
```

### Python
1. Install dependencies for [`pyenv`][https://github.com/pyenv/pyenv/wiki#suggested-build-environment]
2. To avoid manually installing things we can [use][https://github.com/pyenv/pyenv-installer]

### Node.js
We manager our Node.js version with [nvm][https://github.com/nvm-sh/nvm]. Running the command in the Installation section should be enough to install and configure `nvm`.
