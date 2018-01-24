# Global Traefik for *.test

Clone or download to ~/Sites/traefik

Create a self-signed cert

```bash
openssl genrsa 2048 > certs/traefik.key
openssl req -new -x509 -nodes -sha1 -days 3650 -key certs/traefik.key > certs/traefik.cert
```

Fill in your details.
Enter *.test for the Common Name

```bash

openssl x509 -noout -fingerprint -text < certs/traefik.cert > certs/traefik.info
cat certs/traefik.cert certs/traefik.key > certs/traefik.pem
chmod 400 certs/traefik.key certs/traefik.pem
chmod 644 certs/traefik.cert certs/traefik.info
```

Docker up

```bash
docker-compose up -d
```

Traefik should be running always, even after a reboot.

See [Setting up docker4drupal with multiple projects on Mac – Redo](https://www.michaelpporter.com/2017/11/setting-up-docker4drupal-with-multiple-projects-on-mac-redo/) for how to use this with docker4drupal, docker4wordpress or other Docker web-apps.
