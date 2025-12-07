
# 🔍 Network Traffic Analysis – DNS & ICMP Incident Investigation

This project demonstrates a real-world style cybersecurity investigation using **tcpdump**, focusing on DNS (UDP) traffic analysis and ICMP error responses. The goal is to identify the cause behind a website being inaccessible to users.

---

## 📌 **Overview**

A client reported that their website — **[www.yummyrecipesforme.com](http://www.yummyrecipesforme.com)** — was unreachable, displaying the error message:

> **"destination port unreachable"**

As a cybersecurity analyst, your task was to inspect network traffic using `tcpdump` to determine which protocol or service was impacted and to identify the root cause of the incident.

---

## 🧰 **Tools & Technologies Used**

* **tcpdump** (Network packet analyzer)
* **TCP/IP Model**
* **DNS (UDP Port 53)**
* **ICMP (Error handling protocol)**
* **Linux CLI**

---

## 📂 **Project Files**

```
network-traffic-analysis-dns-icmp/
│── README.md                ← you are here
│── incident_report.md       ← full detailed analysis
│── tcpdump-log.txt          ← captured test traffic
│── analysis-diagram.png     ← optional (architecture)
```

---

## 📡 **Scenario Summary**

Users could not access the client’s website. To troubleshoot:

1. You attempted to load the website.
2. Browser sent a **DNS query (UDP)** to resolve the domain name.
3. Instead of receiving a DNS answer, the system received **ICMP "udp port 53 unreachable"** messages.

This indicated that DNS service on the server was not reachable.

---

## 📜 **Captured Log Snippet (from tcpdump)**

```
13:24:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:24:36.098564 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable length 254

13:26:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:27:15.934126 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable length 320

13:28:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:28:50.022967 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable length 150
```

---

## 🧠 **Analysis Summary**

### **✔ Impacted Protocol**

* **DNS over UDP (Port 53)**

### **✔ What Happened**

* DNS queries were sent from the client machine.
* The DNS server responded with ICMP errors:

  * **“udp port 53 unreachable”**

### **✔ Root Cause**

* The DNS server was **not listening on UDP port 53** OR
* A firewall/ACL/network misconfiguration was blocking port 53.

### **✔ Result**

Because DNS resolution failed, the browser **could not obtain the IP address** for the domain → leading to **website inaccessible**.

---

## 📘 **Key Learning Outcomes**

* How DNS queries work over UDP
* How ICMP communicates network-layer errors
* How to read tcpdump logs
* How DNS outages lead to website failure
* How to structure a cybersecurity incident mini-report

---

## 📝 **Incident Report**

A full detailed report is provided in:

```
incident_report.md
```

This includes timestamps, source/destination analysis, protocol breakdown, root cause explanation, and recommendations.

---

## 🚀 **Why This is a Great Portfolio Project**

* Shows **real SOC-style investigation**
* Demonstrates understanding of **network protocols**
* Includes **log analysis**, **troubleshooting**, and **report writing**
* Small, clean, and highly understandable for recruiters

---

## 👍 Author

**Nirakar Mishra**
Cybersecurity Student & Analyst

- 🌐 [Portfolio](https://nirakaramishra-cse.github.io/Portfolio)  

---

