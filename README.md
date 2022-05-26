## [Get this title for $10 on Packt's Spring Sale](https://www.packt.com/V18135?utm_source=github&utm_medium=packt-github-repo&utm_campaign=spring_10_dollar_2022)
-----
For a limited period, all eBooks and Videos are only $10. All the practical content you need \- by developers, for developers

# Cloning the repository
To clone the repository locally, use the following command:
```
git clone https://github.com/PacktPublishing/Software-Security-Testing.git
```
If you do not have Git installed, refer to their [installation pages](https://github.com/git-guides/install-git).

# Installing Docker
All labs in this repository are run using Docker containers and can be pulled from [DockerHub](https://hub.docker.com/u/cyberacademylabs). To download Docker, refer to their [documentation pages](https://docs.docker.com/get-docker/). Installing [docker-compose](https://docs.docker.com/compose/install/) is also preferred.

# Running the labs with docker-compose
## Building and starting the labs
The easiest way to get started is using docker-compose. First, change directory to the cloned repository:
```
cd Software-Security-Testing/
```
Then run the following command:
```
docker-compose up -d
```
After this step, all labs will be up and ready to use. 

## Stopping the labs
To stop the labs, use the following command:
```
docker-compose down
```

# Building the labs 
Docker-compose pulls and builds all labs from DockerHub at once. The labs can be set up individually either by pulling them from DockerHub or by building them locally using the Dockerfiles provided in the GitHub repository. 

## Pulling the labs from DockerHub
Labs can be pulled from DockerHub individually as shown below:
```
docker pull cyberacademylabs/common_web_attacks
```
```
docker pull cyberacademylabs/session_puzzling
```
```
docker pull cyberacademylabs/oracle_padding
```
```
docker pull cyberacademylabs/ldap_injection
```
```
docker pull cyberacademylabs/cors_attack
```
```
docker pull cyberacademylabs/url_redirect
```

After these steps, the Docker images will be pulled locally but the labs will not be active yet. Refer to the 'Starting the Docker containers' section to start the labs.

## Building the Docker images
To build the labs from the Dockerfiles provided, use the following commands:
```
docker build -t cyberacademylabs/common_web_attacks Common\ Web\ Vulnerabilities\ Lab/Common_attacks/
```
```
docker build -t cyberacademylabs/session_puzzling Session\ Puzzling\ Lab/SessionPuzzle/
```
```
docker build -t cyberacademylabs/ldap_injection LDAP\ Injection\ Lab/Ldap-injection/
```
```
docker build -t cyberacademylabs/cors_attack Cross\ Origin\ Resource\ Sharing\ Lab/CORS/
```
```
docker build -t cyberacademylabs/url_redirect URL\ Redirect\ Lab/Url-redirection/
```

## Starting the Docker containers
```
docker run --name common_web_attacks --hostname common_attacks -p 80:80 cyberacademylabs/common_web_attacks
```
```
docker run --name session_puzzling --hostname session_puzzle -p 5000:5000 cyberacademylabs/session_puzzling
```
```
docker run --name oracle_padding --hostname oracle_padding -p 5001:5001 cyberacademylabs/oracle_padding
```
```
docker run --name ldap_injection --hostname ldap_injection -p 5002:5002 cyberacademylabs/ldap_injection
```
```
docker run --name cors_attack --hostname cors_attack -p 5003:5003 cyberacademylabs/cors_attack
```
```
docker run --name url_redirect --hostname redirect -p 5004:5004 cyberacademylabs/url_redirect
```
## Stopping the Docker containers
To stop the running containers, use the following command:
```
docker stop container_name
docker rm container_name
```

# Note
These labs were build to demonstrate security issues. Please make sure to stop the labs once you have completed course exercises.

