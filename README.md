# ossec-EBK
Stack and installation of a ossec-Elastic Search integration to get SIEM/PCI-Dashboard funcionality. 
It uses ElasticSearch new stack (5.0), so Logtash is not required. Please note EBK is used instead ELK

## Stack
1. ossec-Agent Windows  
2. ossec-Agentless Linux configuration  (TBD maybe is easy to work with Agent so not alive notifications are exchanged)
2. ossec-Server Linux installation (Docker)
3. ElasticSearch log ingest via (json output-> Elastic FileBeat -> ElasticIngest.Elastic)

## Deployment Architecture
* On every VM that needs to be monitorized:
 * Windows: Install .exe on every host _ossec-agent-win32-2.8.3.exe_
 * Linux: TBD
* 1 ossec-Server (Linux):  
 * It is based on https://github.com/xetus-oss/docker-ossec-server
 * ossec-server with json output
 * ElasticFileBeat
* 1 ElasticSearch server (Linux)


### Ossec Server

### Windows Agent
- http://ossec.github.io/downloads.html
- version: 2.8.3
- notes

## Quick Start

### ossec Server
* Run oseec server Docker image to get an up and running ossec server that supports auto-enrollment and sends HIDS notifications.
```
docker ps -q -a | xargs docker rm
docker build -t xmltravelgate/ossec-ebk-server:0.0.1 .
docker run --name ossec-ebk-server -d -p 1514:1514/udp -p 1515:1515 -v /var/ossec_mnt:/var/ossec/data xmltravelgate/ossec-ebk-server:0.0.1
```
* Open Server Firewall port 1514

### ossec Agent

## Known Issues / Warnings
- Default Agent (127.0.0.1) is installed due start ossec server error
- 