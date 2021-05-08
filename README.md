# IPA Toolkit <br> <small>platform</small>

The IPA Toolkit implements helpful tools to master the mighty IPA process. This is the platform repository, which contains aids to configure the whole system.

## Getting started
The following steps describe how to set up the IPA toolkit.

### Environment
These steps describe how to set up the system environment on Ubuntu 20.04:

1. Install updates <br> `apt update && apt upgrade`
1. Install Docker dependencies <br> `apt install apt-transport-https ca-certificates curl gnupg lsb-release`
1. Import Dockers GPG key <br> `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`
1. Add Dockers apt repository <br> `echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`
1. Install Docker <br> `apt update && apt install docker-ce docker-ce-cli containerd.io`
1. Download Docker Compose <br> `curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`
1. Give executable permission to Docker Compose <br> `chmod +x /usr/local/bin/docker-compose`
1. Validate the installation of Docker (>= 20.10.6) <br> `docker -v`
1. Validate the installation of Docker Compose (>= 1.29.1) <br> `docker-compose -v`

### Application system
1. Copy the `docker-compose.yml`.
1. Make sure that the DNS is routing all subdomains to the host where the individual services run on.
1. Replace all `example.com` with the domain where the application runs on.
1. Configure the following environment variables:
   - `SECRET_KEY_BASE`: Generate with `rails secret`