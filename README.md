# Docker Reverse Proxy

An nginx based reverse proxy container for routing http requests to various unrelated docker services

## Local ssl cert
https://dockerwebdev.com/tutorials/docker-php-development/

Install `https://github.com/FiloSottile/mkcert`

Create the local Certificate Authority

```bash
mkcert -install
```

Create certs for a domain

```bash
mkcert "*.localhost" localhost 127.0.0.1 ::1
```

Add those certs to your local docker build.

```bash
cp cert.pem ssl/cert.pem
cp cert-key.pem ss/cert-key.pem
```

To move the root cert to another machine (or windows/linux on the same machine) simply copy the CAroot.pem to the location on the new maching and run `mkcert -install` again.  The location of the CAroot.pem can be found with `mkcert -CAROOT`