# 🌐 Rsyslog Forwarding Guide – Send Logs to Remote Server

Learn how to forward logs from one Linux machine to another using `rsyslog`. Perfect for centralizing logs in a homelab, SOC, or SIEM setup.

---

## 🧠 Why Use Log Forwarding?
- Collect logs from multiple systems
- Monitor in one place
- Prepare for SIEM tools like Graylog, ELK, Wazuh, Splunk, etc.

---

## 🧰 Prerequisites
- Two Linux machines (sender + receiver)
- `rsyslog` installed (default on most distros)
- Port `514` (UDP or TCP) open on receiver

---

## 📥 Configure Log Receiver (Server)
Edit `/etc/rsyslog.conf` or drop a file in `/etc/rsyslog.d/remote.conf`

### For UDP:
```bash
module(load="imudp")
input(type="imudp" port="514")
```
### For TCP:
```bash
module(load="imtcp")
input(type="imtcp" port="514")
```
### Optional: Separate Logs by Host
```bash
template(name="RemoteLogs" type="string"
         string="/var/log/remote/%HOSTNAME%/%PROGRAMNAME%.log")
*.* ?RemoteLogs
```
Restart service:
```bash
sudo systemctl restart rsyslog
```

---

## 📤 Configure Log Sender (Client)
Edit `/etc/rsyslog.conf` or `/etc/rsyslog.d/90-remote.conf`

### Send All Logs Over UDP:
```bash
*.* @192.168.1.100:514
```
### Send All Logs Over TCP:
```bash
*.* @@192.168.1.100:514
```
> Use `@` for UDP and `@@` for TCP

Restart sender:
```bash
sudo systemctl restart rsyslog
```

---

## 🔍 Test It
Run a command like:
```bash
echo "Forward test" | logger
```
Then check on the receiver:
```bash
sudo tail -f /var/log/remote/your-client-hostname/*.log
```

---

## 🔐 Security Tips
- Use TCP instead of UDP for reliability
- Use a VPN (WireGuard, Tailscale) to encrypt traffic
- Or configure TLS with rsyslog (advanced)

---

## 📚 Resources
- [rsyslog Docs](https://www.rsyslog.com/doc/)
- [Ubuntu Logging](https://ubuntu.com/server/docs/logging)
- [Graylog Guide](https://docs.graylog.org/)

> 📡 Bonus: Use this with Netdata or Wazuh for real-time dashboards!
