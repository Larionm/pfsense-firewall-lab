# 🔐 pfSense Firewall with pfBlockerNG – Threat Intelligence & Ad Blocking Lab

This project simulates a real-world firewall deployment using **pfSense** and **pfBlockerNG** to protect a local network from malicious IPs, ads, trackers, and known threat domains. It includes hands-on configuration, testing, and logging using a virtual home lab built in **VirtualBox**.

---

## 🧰 Tools & Technologies

- **pfSense 2.7.1** (Community Edition)
- **pfBlockerNG-devel** (threat feed + DNS filtering)
- **VirtualBox**
- **Kali Linux** (as attacker/test machine)
- **DNSBL, IP blocklists, CRON jobs**

---

## 🏗️ Network Architecture

| Component     | IP/Subnet         | Description                |
|---------------|-------------------|----------------------------|
| pfSense WAN   | 192.168.0.x (DHCP) | NAT-facing WAN             |
| pfSense LAN   | 192.168.1.1/24     | Internal LAN Gateway       |
| Kali Linux VM | 192.168.1.100+     | Connected via Internal LAN |

All VMs are hosted in **VirtualBox**, using **Internal Network** mode for isolation and control.

---

## 🔧 Firewall Configuration

### ✅ LAN Rules Created:
- **Block ICMP (Ping)** from any to pfSense
- **Block SSH (TCP 22)** from any to pfSense
- **Logging enabled** for all deny rules

### ✅ pfBlockerNG Setup:
- Installed `pfBlockerNG-devel` via Package Manager
- Configured IP blocking (inbound/outbound)
- Enabled DNSBL with default EasyList/EasyPrivacy
- CRON job scheduled for automatic updates
- Downloaded over **17,000+ IPs/domains**

---

## 🧪 Testing & Results

Tests were performed from the **Kali VM** to simulate external traffic.

| Test                          | Result         |
|-------------------------------|----------------|
| `ping 192.168.1.1`            | Blocked silently (no response) |
| `nc -zv 192.168.1.1 22`       | Connection refused (SSH blocked) |
| `curl http://ads.yahoo.com`  | Block page returned (DNSBL success) |
| pfSense Logs                  | Logged blocked ICMP + SSH attempts |
| pfBlockerNG Reports           | Showed DNSBL blocks + threat feed stats |

---

## 📸 Screenshots

### 🔹 pfSense Dashboard

![pfSense Dashboard](https://github.com/user-attachments/assets/eb687dbd-eba1-4ee9-8278-19e9b90eb1d9)

---

### 🔹 LAN Firewall Rules

![LAN Firewall Rules](https://github.com/user-attachments/assets/45f23ab1-f068-4671-95c0-9ecb7bcfacf7)


---

### 🔹 pfBlockerNG Update & CRON Status

![pfBlockerNG Update](![image](https://github.com/user-attachments/assets/d394d99a-2179-42cf-b7bd-023f50c5d4fa)


---

### 🔹 pfBlockerNG DNSBL Block Test (from Kali)

![DNSBL Block Result](![image](https://github.com/user-attachments/assets/2fa55f8c-b1ae-4b10-92ed-c72998676465)

---

## 📚 Key Takeaways

- ✅ Gained hands-on experience with **firewall rule logic**
- ✅ Used **pfBlockerNG** for real-world IP/domain filtering
- ✅ Practiced **log analysis** and threat validation
- ✅ Simulated malicious activity from Kali to test defenses

---

## 🚀 Future Enhancements

- [ ] Integrate pfSense logs with **Splunk or ELK Stack**
- [ ] Add **GeoIP blocking** (country-level restrictions)
- [ ] Expand blocklists to include additional feeds
- [ ] Script daily backup/export of pfBlockerNG data

---

## 🙌 Credits

Built by [Larion](https://github.com/yourusername)  
Powered by pfSense + pfBlockerNG

