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
docker pull rroemhild/test-openldap
docker run --privileged -d -p 389:389 rroemhild/test-openldap
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

### dc=avengers,dc=com

| Admin            | Secret           |
| ---------------- | ---------------- |
| cn=admin,dc=avengers,dc=com | Endg4m3 |

### ou=heroes,dc=avengers,dc=com

#### cn=Tony Stark,ou=heroes,dc=avengers,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Tony Stark |
| sn               | Stark |
| description      | Human |
| displayName      | Ironman |
| employeeType     | Heroe |
| givenName        | Tony |
| jpegPhoto        | JPEG-Photo (630x507 Pixel, 26780 Bytes) |
| mail             | ironman@avengers.com |
| ou               | heroes |
| uid              | ironman |
| userPassword     | ironman |


### cn=Bruce Banner,ou=heroes,dc=avengers,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Bruce Banner |
| sn               | Banner |
| description      | Human |
| displayName      | Hulk |
| employeeType     | Heroe |
| givenName        | Bruce |
| jpegPhoto        | JPEG-Photo (429x350 Pixel, 22132 Bytes) |
| mail             | hulk@avengers.com |
| ou               | Heroes |
| uid              | hulk |
| userPassword     | hulk |


### cn=Natasha Romanoff,ou=heroes,dc=avengers,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Natasha Romanoff |
| sn               | Romanoff |
| description      | Human |
| displayName      | BlackWidow |
| employeeType     | Heroe |
| givenName        | Natasha |
| jpegPhoto        | JPEG-Photo (343x280 Pixel, 26438 Bytes) |
| mail             | blackwidow@avengers.com |
| ou               | Heroes |
| uid              | blackwidow |
| userPassword     | blackwidow |

### cn=Steve Rogers,ou=heroes,dc=avengers,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Steve Rogers |
| sn               | Rogers |
| description      | Human |
| employeeType     | Heroe |
| givenName        | Steve |
| mail             | cptn-america@avengers.com |
| ou               | Office Management |
| uid              | cptn-america |
| userPassword     | cptn-america |

### cn=Thor,ou=heroes,dc=avengers,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Thor |
| sn               | Thor |
| description      | Demi God |
| employeeType     | Heroe |
| givenName        | Thor |
| mail             | thor@avengers.com |
| ou               | Heroes |
| uid              | thor |
| userPassword     | thor |

### ou=villains,dc=avengers,dc=com

### cn=Thanos,ou=villains,dc=avengers,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Thanos |
| sn               | Thanos |
| description      | Titan Warlord |
| employeeType     | Villain |
| givenName        | Thanos |
| jpegPhoto        | JPEG-Photo (429x350 Pixel, 26526 Bytes) |
| mail             | thanos@avengers.com |
| ou               | Villains |
| uid              | thanos |
| userPassword     | thanos |

### cn=Bender Bending Rodríguez,ou=people,dc=avengers,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Bender Bending Rodríguez |
| sn               | Rodríguez |
| description      | Robot |
| employeeType     | Ship's Robot |
| givenName        | Bender |
| jpegPhoto        | JPEG-Photo (436x570 Pixel, 26819 Bytes) |
| mail             | bender@avengers.com |
| ou               | Delivering Crew |
| uid              | bender |
| userPassword     | bender |

### cn=Amy Wong+sn=Kroker,ou=people,dc=avengers,dc=com

Amy has a multi-valued DN

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | inetOrgPerson |
| cn               | Amy Wong |
| sn               | Kroker |
| description      | Human |
| givenName        | Amy |
| mail             | amy@avengers.com |
| ou               | Intern |
| uid              | amy |
| userPassword     | amy |

### cn=admin_staff,ou=people,dc=avengers,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | Group |
| cn               | admin_staff |
| member           | cn=Hubert J. Farnsworth,ou=people,dc=avengers,dc=com |
| member           | cn=Hermes Conrad,ou=people,dc=avengers,dc=com |

### cn=ship_crew,ou=people,dc=avengers,dc=com

| Attribute        | Value            |
| ---------------- | ---------------- |
| objectClass      | Group |
| cn               | ship_crew |
| member           | cn=Turanga Leela,ou=people,dc=avengers,dc=com |
| member           | cn=Philip J. Fry,ou=people,dc=avengers,dc=com |
| member           | cn=Bender Bending Rodríguez,ou=people,dc=avengers,dc=com |
