Understanding and Detecting DNS inconsistencies.

Computers don’t understand what a “domain” is, but they do understand the IP.  DNS helps computers locate resources.  Basically – DNS translates domain names to IP addresses.  DNS servers do this translation and can reside inside an enterprise network, as well as out in the wild (internet service providers, other organizations, malicious actors, etc).
DNS uses both UDP and TCP on port 53 for communications. 
TCP will be used for payloads over 512 bytes and for zone transfers. 
DNS uses a hierarchical system to determine the correct IP address for a domain.
When data exfiltration occurs-- attackers want to hide their data transfer in the noise of all the other DNS requests.  It is uncommon to see DNS requests with more than 512 bytes using TCP, because it would be much easier to detect those.

Quick wins:
Baseline (Traffic Analysis)
If host A normally does 200 DNS requests per day and all of a sudden this number goes up to 600 we can pull the data to understand what IP/location is making the requests. 

<img src="/images/baseline-traffic-analysis.png?raw=true"/> 

This graph shows Splunk traffic with a large spike in DNS traffic.

<img src="/images/splunk-dns-traffic.png?raw=true"/> 


This chart shows varying requests and their count.  Is it normal to see large spikes in DNS requests in off-hours?
Statistical techniques (Payload Analysis)
Look at DNS requests for unusual data being sent/sent back.  Varying payload sizes ( > 512 bytes?)
Is there additional data in the requests?  Example:  examplesite.com/oddURI/lookslikeapassword/maybethispartisinbase64/etc

<img src="/images/payload-analysis.png?raw=true"/> 

Bonus things to look for:
•	Increase in volume of requests by the client (indicating C&C or data movement)
•	Change in the type of resource records we see (e.g., TXT records from hosts that don’t typically send them)
•	Variance in the length of the request (indicating DGA or encoded/obfuscated data stream)
•	Variability in the frequency of requests (Beaconing activity to C&C)
•	Randomness in domain names (DGA)
	https://www.splunk.com/en_us/blog/tips-and-tricks/you-can-t-hyde-from-dr-levenshtein-when-you-use-url-toolbox.html
•	Substitution of domains to very slightly altered domains (typo-squatting)

Top 10 Clients by Volume of Requests
tag=dns message_type="Query" 
| timechart span=1h limit=10 usenull=f useother=f count AS Requests by src

Packet Size & Volume Distribution
tag=dns message_type="QUERY"
| mvexpand query
| eval queryLength=len(query)
| stats count by queryLength, src
| sort -queryLength, count
| table src queryLength count
| head 1000

Beaconing Activity
tag=dns message_type="QUERY"
| fields _time, query
| streamstats current=f last(_time) as last_time by query
| eval gap=last_time - _time
| stats count avg(gap) AS AverageBeaconTime var(gap) AS VarianceBeaconTime BY query
| eval AverageBeaconTime=round(AverageBeaconTime,3), VarianceBeaconTime=round(VarianceBeaconTime,3)
| sort -count
| where VarianceBeaconTime < 60 AND count > 2 AND AverageBeaconTime>1.000
| table  query VarianceBeaconTime  count AverageBeaconTime


Number of Hosts Talking to Beaconing Domains
tag=dns message_type="QUERY"
| fields _time, src, query
| streamstats current=f last(_time) as last_time by query
| eval gap=last_time - _time
| stats count dc(src) AS NumHosts avg(gap) AS AverageBeaconTime var(gap) AS VarianceBeaconTime BY query
| eval AverageBeaconTime=round(AverageBeaconTime,3), VarianceBeaconTime=round(VarianceBeaconTime,3)
| sort –count
| where VarianceBeaconTime < 60 AND AverageBeaconTime > 0


Domains with Lots of Sub-Domains
tag=dns message_type="QUERY"
 | eval list="mozilla"
 | `ut_parse_extended(query, list)`
 | stats dc(ut_subdomain) AS HostsPerDomain BY ut_domain
 | sort -HostsPerDomain

DNS queries to randomized subdomains
sourcetype=stream:dns host=<host name> record_type=A
|table query{}
|lookup ut_parse_extended_lookup url AS query{}
|search ut_domain!=None NOT (ut_domain_without_tld=microsoft OR ut_domain_without_tld=msn OR ut_domain_without_tld=windows.com OR ut_domain_without_tld=qwest.net)
|`ut_shannon(ut_subdomain)`
|stats count BY query{} ut_subdomain ut_domain ut_domain_without_tld ut_tld ut_shannon
|sort - ut_shannon


Search explanation
___________________________________________________________________________________
|Splunk Search           |Explanation                        			  |
|---   	                 |---                                		          |
|sourcetype=stream:dns   |Search only Stream DNS data.         	   	          |
|host=<host name> 	 |Search data from a specified host only.		  |
|record_type=A		 |Search only DNS A records, which return IPv4 addresses. |
|table query{}	         |Display the results in a table with the query{} column. |	
___________________________________________________________________________________

	
