# Anti DDoS Script v2.0

This is my script to help you with your machine. It includes Anti-DDoS auto install tool, and System Update/Upgrade integrated.

It was tested on Debian 12 system, where it was proven successful.(\*)

---
#### History about the script

Script was first created back in May 2020. and has now received it's update on 25.11.2024.
It includes the features for blocking floods, and strange packets that are incomplete/invalid.

---
#### Explanation of the script

The script utilizes **iptables** to create the rules for all the traffic that does not seem legit and might be malicious.
By default rules of this script **ALL** traffic is dropped on the ports that are not specifically set up to allow connection to them. For allowing additional ports you will have to edit the script yourself.

Sample line for opening port 8080:
```bash
# Incoming traffic for both TCP and UDP
"$IPTABLES" -A INPUT -m state --state NEW -p tcp --dport 8080 -j ACCEPT
"$IPTABLES" -A INPUT -m state --state NEW -p udp --dport 8080 -j ACCEPT

# Outcoming traffic for both TCP and UDP
"$IPTABLES" -A OUTPUT -m state --state NEW -p tcp --dport 8080 -j ACCEPT
"$IPTABLES" -A OUTPUT -m state --state NEW -p udp --dport 8080 -j ACCEPT
```

For any other options of iptables you should refer to the [iptables Documentation](https://linux.die.net/man/8/iptables).

---

# Usage:

To use and set up the script, do the following:
```bash
sudo apt-get install git iptables -y
git clone https://github.com/dnllzc/Anti-DDoS-v2.git
cd Anti-DDoS-v2/
chmod +x Anti-DDoS-v2
sudo ./Anti-DDoS-v2
```
and follow the script options.

---

###### (\*)Note: This script is not 100% of the time successful in stopping all forms of a DoS/DDoS attacks.

---
