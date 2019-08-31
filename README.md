# on-fleek
Automated installation script for the FLEEK stack (Filebeat, Logstash, Elasticsearch, Elastic APM Server and Kibana) on Ubuntu 18.04 (bionic).

Produced for a sydjango meetup talk concentrating on Elastic APM, `on-fleek` installs the entire FLEEK stack on any Ubuntu 18.04 installation with little user input.

## FLEEK?
Yes, FLEEK. It stands for:

**F**ilebeat<br>
**L**ogstash<br>
**E**lasticsearch<br>
**E**lastic APM Server<br>
**K**ibana

## Why?
Getting all of the parts of the FLEEK stack talking to each other and working in harmony is often a barrier to entry that makes a lot of people give up before being able to test out all FLEEK has to offer. 

## What does this script do?
This script installs OpenJDK 11 and the FLEEK stack. As an added bonus, Kibana is placed behind nginx with basic authentication enabled and an auto-renewing certbot SSL certificate is enabled on the FQDN.

## Setup Instructions
0. A fresh install or instance of Ubuntu 18.04 should be used. This script installs `openjdk-11-jre` which is required by the FLEEK stack.
1. Clone this repository into a folder using `git clone https://github.com/bartonip/on-fleek`. 
2. Go into the folder using `cd on-fleek`.
3. Assign execution permissions to the `on-fleek` script using `chmod +x on-fleek`.
4. This script must be run as sudo, so run it using `sudo ./on-fleek` to begin the installation.

The installation is mostly unattended with the exception of the entry of a username/password for Kibana and FQDN for the SSL Certificate. 

## What ports are the services on?
**F**ilebeat: No port as it listens for files.
**L**ogstash: 0.0.0.0:5040 [TCP]
**E**lasticsearch: localhost:9200 [TCP]
**E**lastic APM Server: 0.0.0.0:8200 [TCP]
**K**ibana: localhost:5060 [TCP], proxied by nginx on 0.0.0.0:80/443 [TCP]

## Where to from here?
All of Elasticsearch's logging and performance monitoring goodness has been installed. Connect your application to Elastic APM to start monitoring right away, or connect your application's logstream to Logstash either directly or through Filebeat to start analysing your logs now.
