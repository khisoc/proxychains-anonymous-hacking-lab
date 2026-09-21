# Proxychains & Tor Anonymous Networking Lab

> **University of Technology, Jamaica**  
> Course: **Computer Security (CIT4020)**

This project demonstrates how to configure **Proxychains** with the **Tor** network to anonymize network traffic for cybersecurity testing in a controlled lab environment.

## Technologies

- Kali Linux / Ubuntu
- Proxychains4
- Tor
- SOCKS5 Proxy
- Lynx
- WHOIS

## Lab Objectives

1. Update Proxychains.
2. Install Tor.
3. Configure Proxychains to use Tor via SOCKS5.
4. Verify anonymous routing.
5. Perform a WHOIS query through Proxychains.
6. Answer analysis questions on anonymity and ethics.

## Lab Workflow

### 1. Update Proxychains

```bash
sudo apt update
sudo apt install proxychains4
```

### 2. Install Tor

```bash
sudo apt install tor
sudo systemctl enable tor
sudo systemctl start tor
```

### 3. Configure Proxychains

Edit the configuration file.

```bash
sudo nano /etc/proxychains4.conf
```

Important changes:

- Enable `dynamic_chain`
- Disable `strict_chain`
- Replace SOCKS4 with:

```text
socks5 127.0.0.1 9050
```

### 4. Start Tor & Test

```bash
sudo systemctl status tor
proxychains curl ifconfig.me
```

The IP returned should differ from the local IP because traffic is routed through the Tor network.

### 5. Browser Verification

Install Lynx.

```bash
sudo apt install lynx
proxychains lynx dnsleaktest.com
```

This confirms DNS requests are routed through Tor.

### 6. WHOIS Query

```bash
proxychains whois example.com
```

The WHOIS lookup is performed through the Tor proxy rather than directly from the local host.

## Lab Questions (Summary)

| Question | Summary |
|---|---|
| Why update Proxychains? | Ensures latest proxy configuration and security fixes. |
| Why use Tor? | Routes traffic through multiple relay nodes for anonymity. |
| Dynamic vs Strict Chain | Dynamic skips dead proxies; Strict fails if one proxy is unavailable. |
| SOCKS4 vs SOCKS5 | SOCKS5 supports authentication and more protocols. |
| IP Difference | Tor exit node IP replaces the original IP address. |
| WHOIS via Proxychains | Masks the source of the network query. |
| Real-world Uses | Penetration testing, privacy research, censorship circumvention. |
| Limitations | Tor traffic can still be detected or blocked by IDS/firewalls. |
| Ethics | Appropriate for authorized security testing and privacy, not malicious activity. |

## Screenshots

All screenshots extracted from the original report are located in `images/`.

Total screenshots extracted: **12**.

## Skills Demonstrated

- Anonymous network routing.
- Proxy configuration.
- Tor network usage.
- SOCKS5 proxy setup.
- IP and DNS leak testing.
- Network reconnaissance through anonymized channels.

## Author

**Mekhi Bentley**  
Student ID: **2304855**
