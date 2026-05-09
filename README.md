# WIreshark-Traffic-Analysis

---

## **Analyzing a Real-World PCAP with Wireshark**

In this project, I analyzed the file 2024-11-26-traffic-analysis-exercise.pcap2 using Wireshark. The PCAP contained network traffic from a host infected with NetSupport RAT (Remote Access Trojan).

The following alerts for NetSupportRAT were triggered:

![Wireshark 1](wireshark1.png)

## **Investigation Approach**

The analysis followed a structured process:

1. Started with a high-level overview of the traffic to identify interesting patterns and conversations.
2. Narrowed the scope to specific IP addresses and protocols.
3. Applied filters to uncover indicators of compromise (IOCs).

To begin, open the PCAP file in Wireshark:

![Wireshark 1](wireshark2.png)

---

## **Traffic Filtering and Analysis**

Step 1: Filtering Traffic

Using the “Basic” filter button configured earlier, I was able to view successful connections and reduce the packet count from:

- 2,922 packets
to
- 173 packets

This helped narrow the investigation scope and focus on suspicious:

![Wireshark 1](wireshark8.png)

Step 2: Following TCP Stream

Once l have discovered the session with the suspicious IP address that triggered the alert, l can right click that packet and “Follow TCP Stream".

![Wireshark 1](wireshark3.png) 

Step 3: Reviewing the HTTP POST Request

By reviewing the header, l discover two interesting entries in the POST request. The first one is the URL 194.180.191.64/fakeurl[.]htm. The second item of interest is the User Agent String, NetSupport Manager.  The NetSupport service is known to be widely abused and used in NetSupportRAT. If your organization does not use this service, this is almost certainly malicious activity.

![Wireshark 1](wireshark4.png) 

Pivoting to open source research, using VirusTotal, l confirm that 194[.]180[.]191[.]64/fakeurl[.]htm is associated with NetSupportRAT malicous activity.

![Wireshark 1](wireshark5.png) 
![Wireshark 1](wireshark6.png) 

Step 4: Victim Identification

To identify the victim, I applied the following LDAP filter:

```Wireshark
 ldap contains "givenName"
```

The analysis revealed the victim user as:

```Wireshark
 Oliver Boonwall
```
![Wireshark 1](wireshark7.png) 

--- 

## **Conclusion**

This investigation demonstrated how Wireshark can be used to:

Analyze PCAP files
Filter suspicious traffic
Follow TCP streams
Identify indicators of compromise
Investigate malware-related communications

l have demonstrated that Wireshark can be used to analyze pcap files, as well as capture them. 






































