English | [简体中文](./README.zh-CN.md)
# suricata-rules
	Suricata is an excellent open source intrusion detection system that records the high quality Suricata IDS rules 
	extracted by security operations staff. Welcome to submit 

### Rules are written as follows
Each rule corresponds to the new directory as follows

	webshell detect	#Rule directory name - clearly described according to the corresponding detection rules
	- webshell.pcap	#The pcap package corresponding to the rule is saved as much as possible in the form of flow.
	- websehll.rules	#The rule file extracted by yourself, try to test the submission.
	- README	#Can describe some rules related things, easy for others to understand, support Markdown

#### Rule directory
	The directory is named after a single CVE, hacking tool, threat type. If there is a corresponding rule directory, 
	it is recommended to store it in the existing rule directory.

#### The rule corresponds to the pcap package
	After the pcap corresponding to the rule is filtered by Wireshark, use the menu file 
	-- save a specific group -- to select the pcap format to upload.
Easy to identify malicious streaming data, also minimal, easy to move and backup

#### rule.rules
	The rules file is named randomly, but the suffix must be rules, such as: webshell_caidao.rules
Multiple rule files can appear in the file, as stated in the README note
The rules are recommended as follows：
##### Example
	sid：
	0~1000000   Sourcefire VRT
	2000001~2999999     EMerging Threats(ET)
	3000000~3999999     public
	Network scanning    3000000～3000999
	Violent cracking    3001000～3001999
	Exploit    3002000～3002999
	Back door    3003000～3003999
	WebShell    3004000～3004999
	Virus Trojan    3005000～3005999
	Spyware    3006000～3006999
	safety certificate    3007000～3007999
	Code execution    3008000～3008999
	File restore    3009000～3009999
	file transfer    3010000～3010999
	Suspicious DNS    3011000～3011999
	HTTP    3012000～3012999
	Malicious behavior    3013000～3013999
	Violation operation    3014000～3014999
	Sensitive information leakage    3015000～3015999
	Hacking tool    3016000～3016999
	Rev is incremented for each version of the rule version, metadata added creation date and creator
	Reference is a reference source/reference material, such as a CVE number, or a fix, an attack description,
	and so on.
	alert http any any -> any any (msg:"webshell_caidao_php"; flow:established; content:"POST";
    http_method; content:".php"; http_uri; content:"base64_decode"; http_client_body;  sid:3004001; 
    rev:1; metadata:created_at 2018_11_14, by al0ne;)

# Note
Description of the root directory file of this project

	suricata-ids.rules	#A collection of all rules, directly downloading rule file replacements when updating.
	disable.conf	#Suricata disable rules are recorded during analysis (invalid, false positives, etc.)
	sid.txt 	#The sid of all rules is recorded to avoid duplication, and the sid.txt file must be updated 
	each time the rule is added.
