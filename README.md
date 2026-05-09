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
















