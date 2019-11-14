# OpenLDAP Docker Image for testing

![Docker Build Status](https://img.shields.io/docker/build/rroemhild/test-openldap.svg) ![Docker Stars](https://img.shields.io/docker/stars/rroemhild/test-openldap.svg) ![Docker Pulls](https://img.shields.io/docker/pulls/rroemhild/test-openldap.svg)

This image provides an OpenLDAP Server for testing LDAP applications, i.e. unit tests. The server is initialized with the example domain `avengers.com` with data from the [Marvel Wiki].

Parts of the image are based on the work from Nick Stenning [docker-slapd][slapd] and Bertrand Gouny [docker-openldap][openldap].

The Flask extension [flask-ldapconn][flaskldapconn] use this image for unit tests.

[slapd]: https://github.com/nickstenning/docker-slapd
[openldap]: https://github.com/osixia/docker-openldap
[flaskldapconn]: https://github.com/rroemhild/flask-ldapconn
[futuramawikia]: http://futurama.wikia.com


## Features

* Initialized with data from Futurama
* Support for TLS (snake oil cert on build)
* memberOf overlay support
* MS-AD Style Groups support
* ~124MB images size (~40MB compressed)


## Usage

```
docker pull carlosrbcunha/docker-test-openldap
docker run --privileged -d -p 389:389 carlosrbcunha/docker-test-openldap
```

## Exposed ports

* 389
* 636

## Exposed volumes

* /etc/ldap/slapd.d
* /etc/ldap/ssl
* /var/lib/ldap
* /run/slapd


## LDAP structure

### dc=marvel,dc=com

| Admin            | Secret           |
| ---------------- | ---------------- |
| cn=admin,dc=marvel,dc=com | BestPasswordEver |

### ou=heroes,dc=marvel,dc=com

#### cn=Tony Stark,ou=heroes,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Tony Stark |
| sn               | Stark |
| description      | Human |
| displayName      | Ironman |
| employeeType     | Heroe |
| givenName        | Tony |
| mail             | ironman@marvel.com |
| ou               | heroes |
| uid              | ironman |
| userPassword     | ironman |


### cn=Bruce Banner,ou=heroes,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Bruce Banner |
| sn               | Banner |
| description      | Human |
| displayName      | Hulk |
| employeeType     | Heroe |
| givenName        | Bruce |
| mail             | hulk@marvel.com |
| ou               | Heroes |
| uid              | hulk |
| userPassword     | hulk |


### cn=Natasha Romanoff,ou=heroes,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Natasha Romanoff |
| sn               | Romanoff |
| description      | Human |
| displayName      | BlackWidow |
| employeeType     | Heroe |
| givenName        | Natasha |
| mail             | blackwidow@marvel.com |
| ou               | Heroes |
| uid              | blackwidow |
| userPassword     | blackwidow |

### cn=Steve Rogers,ou=heroes,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Steve Rogers |
| sn               | Rogers |
| description      | Human |
| employeeType     | Heroe |
| givenName        | Steve |
| mail             | cptn-america@marvel.com |
| ou               | Office Management |
| uid              | cptn-america |
| userPassword     | cptn-america |

### cn=Thor,ou=heroes,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Thor |
| sn               | Thor |
| description      | Demi God |
| employeeType     | Heroe |
| givenName        | Thor |
| mail             | thor@marvel.com |
| ou               | Heroes |
| uid              | thor |
| userPassword     | thor |

### ou=villains,dc=marvel,dc=com

### cn=Thanos,ou=villains,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Thanos |
| sn               | Thanos |
| description      | Titan Warlord |
| employeeType     | Villain |
| givenName        | Thanos |
| mail             | thanos@thanos.com |
| ou               | Villains |
| uid              | thanos |
| userPassword     | thanos |

### cn=Johann Schmidt,ou=villains,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Johann Schmidt |
| sn               | Schmidt |
| description      | Human |
| employeeType     | Hydra |
| givenName        | Johann |
| mail             | redskull@marvel.com |
| ou               | Villains |
| uid              | redskull |
| userPassword     | redskull |

### cn=Arnin Zola,ou=villains,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Arnin Zola |
| sn               | Zola |
| description      | Human |
| givenName        | Arnin |
| mail             | zola@marvel.com |
| ou               | Villains |
| uid              | zola |
| userPassword     | zola |

### cn=Alexander Pierce,ou=villains,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Alexander Pierce |
| sn               | Pierce |
| description      | Human |
| givenName        | Alexander |
| mail             | pierce@marvel.com |
| ou               | Villains |
| uid              | pierce |
| userPassword     | pierce |

### cn=Wolfgang von Strucker,ou=villains,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Wolfgang von Strucker |
| sn               | Strucker |
| description      | Human |
| givenName        | Wolfgang |
| mail             | strucker@marvel.com |
| ou               | Villains |
| uid              | strucker |
| userPassword     | strucker |

### cn=Werner Reinhardt,ou=villains,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Werner Reinhardt |
| sn               | Reinhardt |
| description      | Human |
| givenName        | Werner |
| mail             | reinhardt@marvel.com |
| ou               | Villains |
| uid              | reinhardt |
| userPassword     | reinhardt |

### cn=Peter Quill,ou=heroes,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Peter Quill |
| sn               | Quill |
| description      | Human |
| givenName        | Peter |
| mail             | quill@gmarvel.com |
| ou               | Guardians |
| uid              | quill |
| userPassword     | quill |

### cn=Rocket Raccoon,ou=heroes,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Rocket Raccoon |
| sn               | Raccoon |
| description      | Halfworlder |
| givenName        | Werner |
| mail             | rocket@marvel.com |
| ou               | Guardians |
| uid              | rocket |
| userPassword     | rocket |

### cn=Groot,ou=heroes,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Groot |
| sn               | Groot |
| description      | Flora colossus |
| givenName        | Baby |
| mail             | groot@marvel.com |
| ou               | Guardians |
| uid              | groot |
| userPassword     | groot |

### cn=Drax the Destroyer,ou=heroes,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Drax the Destroyer |
| sn               | Destroyer |
| description      | Male |
| givenName        | Drax |
| mail             | drax@marvel.com |
| ou               | Guardians |
| uid              | drax |
| userPassword     | drax |

### cn=Mantis,ou=heroes,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Mantis |
| sn               | Mantis |
| description      | Female |
| givenName        | Mantis |
| mail             | mantis@marvel.com |
| ou               | Guardians |
| uid              | mantis |
| userPassword     | mantis |

### cn=Avengers,ou=groups,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | Group |
| cn               | Avengers |
| member           | cn=Tony Stark,ou=heroes,dc=marvel,dc=com |
| member           | cn=Bruce Banner,ou=heroes,dc=marvel,dc=com |
| member           | cn=Natasha Romanoff,ou=heroes,dc=marvel,dc=com |
| member           | cn=Steve Rogers,ou=heroes,dc=marvel,dc=com |
| member           | cn=Thor,ou=heroes,dc=marvel,dc=com |

### cn=Hydra,ou=groups,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | Group |
| cn               | Hydra |
| member           | cn=Johann Schmidt,ou=villains,dc=marvel,dc=com |
| member           | cn=Arnin Zola,ou=villains,dc=marvel,dc=com |
| member           | cn=Alexander Pierce,ou=villains,dc=marvel,dc=com |
| member           | cn=Wolfgang von Strucker,ou=villains,dc=marvel,dc=com |
| member           | cn=Werner Reinhardt,ou=villains,dc=marvel,dc=com |

### cn=Guardians,ou=groups,dc=marvel,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | Group |
| cn               | Guardians |
| member           | cn=Peter Quill,ou=heroes,dc=marvel,dc=com |
| member           | cn=Rocket Raccoon,ou=heroes,dc=marvel,dc=com |
| member           | cn=Groot,ou=heroes,dc=marvel,dc=com |
| member           | cn=Drax the Destroyer,ou=heroes,dc=marvel,dc=com |
| member           | cn=Mantis,ou=heroes,dc=marvel,dc=com |