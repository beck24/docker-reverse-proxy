# Docker Reverse Proxy

An nginx based reverse proxy container for routing http requests to various unrelated docker services

## Build

Copy the docker-override template and set any env specific values

```bash
cp docker-compose.override.yml.example docker-compose.override.yml
```

Create any virtual hosts by copying the template and editing it

```bash
cp templates/default.conf.template.example mysite.conf.template
```

Once docker containers are up and running and configured to connect on the network "nginx-router" bring up this router

```bash
docker compose up -d
```

## Local ssl cert
https://dockerwebdev.com/tutorials/docker-php-development/

Install `https://github.com/FiloSottile/mkcert`

Create the local Certificate Authority

```bash
mkcert -install
```

Create certs for a domain

```bash
cd certs/
mkcert "*.localhost" localhost 127.0.0.1 ::1
```

To move the root cert to another machine (or windows/linux on the same machine) simply copy the CAroot.pem to the location on the new maching and run `mkcert -install` again.  The location of the CAroot.pem can be found with `mkcert -CAROOT`