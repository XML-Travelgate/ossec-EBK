# ossec-EK
Stack and installation of a ossec-Elastic Search integration to get SIEM/PCI-Dashboard funcionality. 
It uses ElasticSearch new stack (5.0), so Logtash is not required. Please note EK is used instead ELK

## Stack
1. ossec-Agent Windows  
2. ossec-Agentless Linux configuration  (TBD maybe is easy to work with Agent so not alive notifications are exchanged)
2. ossec-Server Linux installation (Docker)
3. ElasticSearch log ingest via (json output-> Elastic FileBeat -> ElasticIngest.Elastic)

## Deployment Architecture
* On every VM that needs to be watched:
 * Windows: Install .exe on every host _ossec-agent-win32-2.8.3.exe_
 * Linux: TBD
* 1 server or cluster:
 * 
ossec-Server
  * Only Linux:  







### Ossec Server

### Windows Agent
- http://ossec.github.io/downloads.html
- version: 2.8.3
- notes
