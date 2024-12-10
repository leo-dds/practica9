# practica9 https://github.com/leo-dds/practica9.git
1.-Este es el docker-compose que utilizado para hacer este actividad 
~~~
asr@asr-VirtualBox:~/composer$ cat docker-compose.yml 
version: '3.8'

services:
  web:
    image: php:7.4-apache
    container_name: apache_server
    ports:
      - "8080:80"
    volumes:
      - ./www:/var/www
      - ./confApache:/etc/apache2
    networks:
      apache_red:
        ipv4_address: 192.168.0.20

  dns:
    container_name: dns_server
    image: ubuntu/bind9
    ports:
      - "5353:53/udp"  # Porto DNS precisa ser UDP
      - "5353:53/tcp"
    volumes:
      - ./confDNS/conf:/etc/bind
      - ./confDNS/zonas:/var/lib/bind
    networks:
      apache_red:
        ipv4_address: 192.168.0.3

networks:
  apache_red:
    driver: bridge
    ipam:
      driver: default
      config:
        - subnet: 192.168.0.0/24
~~~
NO CONSEGUI COMPLETAR LA ACTIVIDAD SIN ERRORES 
asr@asr-VirtualBox:~$ cd composer/
asr@asr-VirtualBox:~/composer$ tree
.
├── apache
│   ├── conf
│   │   ├── fabulasmaravillosas.conf
│   │   ├── fabulasoscuras.conf
│   │   └── httpd.conf
│   ├── Dockerfile
│   └── htdocs
│       ├── fabulasmaravillosas
│       │   ├── index.html
│       │   └── index.html.save
│       └── fabulasoscuras
│           └── index.html
├── bind9_subnet.json
├── conf
│   ├── fabulasmaravillosas.conf
│   ├── fabulasoscuras.conf
│   ├── named.conf
│   ├── named.conf.default-zones
│   ├── named.conf.local
│   └── named.conf.options
├── confApache
├── confDNS
│   ├── conf
│   └── zonas
├── docker-compose.yml
├── docker-compose.yml.save
├── imagenes
│   └── captura.png
├── Readme.md
├── README.md
├── www
│   ├── html
│   └── index.html
└── zonas
    ├── db.asircastelao.int
    ├── db.fabulasmaravillosas
    └── db.fabulasoscuras

