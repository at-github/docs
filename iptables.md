# iptables

Display current rules
`iptables -L`
or with line number `iptables -L --line-number`

Some arguments explain
- `-A` Append one or more rules
- `-p` Protocol of the rule
- `-i` Interface name
- `-j` Target of the rule, what to do with the matched packet
- `-d` Destination address

Reset rules
```
iptables -F
iptables -X
```
Allow current connection
`iptables -A INPUT -m conntrack --ctstate ESTABLISHED -j ACCEPT`

Allow incoming traffic on specific port like ssh
`iptables -A INPUT -p tcp -i eth0 --dport ssh -j ACCEPT`

Allow all web incoming traffic
`iptables -A INPUT -p tcp -i eth0 --dport 80 -j ACCEPT`
`iptables -A INPUT -p tcp -i eth0 --dport 443 -j ACCEPT`

Delete a rule for INPUT with the specific line number
`iptables -D INPUT 5`
