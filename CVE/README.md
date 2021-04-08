## What is Suricata?
Suricata is a free and open source, mature, fast and robust network threat detection engine.  
For more information, go to https://suricata-ids.org/.
## The purpose of this repository
* Supporting blue team members writing Suricata rules for the new critical vulnerabilities to detect and prevent the exploitation of attackers as soon as possible.
* Updating Suricata rules regularly and holding them in a well-managed database.
## The content structure
Each vulnerability owns a folder.  
Each folder has 2 main parts:
* The file README.md includes 3 parts:
  * Overview of the vulnerability
  * Proof of Concept (PoC) or in other words, the samples of the malicious payloads
  * References
* The file .rules holds the Suricata rule itself.
## Notes
* Many services run on HTTPS but Suricata cannot analyze encrypted data. If you want to use Suricata to detect attackers in your HTTPS payload, you should set up a reverse proxy for HTTPS like nginx, then forward HTTP to your application servers, and run Suricata on this HTTP traffic.
* Instead of **any any -> any any**, you can set your own networks and ports configuration if you are sure about your system usage. For example, you have an HTTP server runs only on port 8443 and receives traffic from $HOME_NET, it will be **any any -> $HOME_NET 8443**.
* You should change the **sid** to match your own configuration. In this repository, I often use a nearly random value for this field.
## Want to support its development?
Buy me a coffee via Paypal: https://paypal.me/sudoka
## Refs

1. https://github.com/sudohyak/suricata-rules