![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:ip
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -D INPUT -m set --match-set ipsum src -j DROP 2>/dev/null
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2024-03-28)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
185.224.128.34|-|10
45.155.91.99|-|10
178.20.55.16|marcuse.nos-oignons.net|10
122.224.37.86|-|10
150.230.133.120|-|9
185.129.62.63|tor02.zencurity.com|9
80.67.172.162|algrothendieck.nos-oignons.net|9
80.82.77.33|sky.census.shodan.io|8
138.19.2.243|138019002243.ctinets.com|8
167.94.146.60|-|8
167.248.133.190|scanner-29.ch1.censys-scanner.com|8
186.96.145.241|fixed-186-96-145-241.totalplay.net|8
167.248.133.35|scanner-08.ch1.censys-scanner.com|8
167.248.133.51|scanner-09.ch1.censys-scanner.com|8
183.81.169.238|-|8
158.51.96.38|unknown.ip-xfer.net|8
167.94.138.52|scanner-07.ch1.censys-scanner.com|8
167.94.146.51|-|8
167.94.146.57|-|8
93.174.95.106|battery.census.shodan.io|8
36.110.228.254|-|8
162.142.125.10|scanner-04.ch1.censys-scanner.com|8
167.248.133.52|scanner-09.ch1.censys-scanner.com|8
167.94.138.124|scanner-27.ch1.censys-scanner.com|8
167.94.138.127|scanner-27.ch1.censys-scanner.com|8
167.94.138.50|scanner-07.ch1.censys-scanner.com|8
194.169.175.36|-|8
194.169.175.35|-|8
167.248.133.49|scanner-09.ch1.censys-scanner.com|8
87.98.138.142|ip142.ip-87-98-138.eu|8
190.144.14.170|-|8
185.129.62.62|tor01.zencurity.com|8
119.206.117.30|-|8
167.248.133.127|scanner-26.ch1.censys-scanner.com|8
71.6.135.131|soda.census.shodan.io|8
104.230.97.51|104-230-097-051.res.spectrum.com|8
167.94.145.56|-|8
167.94.145.51|-|8
167.94.145.53|-|8
167.94.145.52|-|8
112.167.233.14|-|8
121.177.70.228|-|7
123.203.108.104|123203108104.ctinets.com|7
87.236.176.72|timely.monitoring.internet-measurement.com|7
220.74.78.244|-|7
89.234.157.254|marylou.nos-oignons.net|7
71.6.199.23|einstein.census.shodan.io|7
221.226.39.202|-|7
196.20.68.81|-|7
218.92.0.34|-|7
218.92.0.31|-|7
203.205.37.233|static.cmcti.vn|7
84.2.226.70|ktv5402e246.fixip.t-online.hu|7
94.102.49.193|cloud.census.shodan.io|7
147.78.103.179|-|7
213.6.203.226|-|7
193.32.162.12|mail.subit.cc|7
64.227.126.250|-|7
220.88.1.208|-|7
167.172.230.140|-|7
165.227.166.247|-|7
162.142.125.221|scanner-25.ch1.censys-scanner.com|7
162.142.125.220|scanner-25.ch1.censys-scanner.com|7
162.142.125.222|scanner-25.ch1.censys-scanner.com|7
162.142.125.226|scanner-25.ch1.censys-scanner.com|7
218.92.0.76|-|7
167.248.133.50|scanner-09.ch1.censys-scanner.com|7
138.68.9.83|-|7
87.255.193.50|-|7
171.25.193.77|tor-exit-read-me.dfri.se|7
218.92.0.107|-|7
82.200.65.218|gw-bell-xen.ll-nsk.zsttk.ru|7
200.122.249.203|static-dedicado-200-122-249-203.une.net.co|7
167.248.133.36|scanner-08.ch1.censys-scanner.com|7
87.236.176.225|exhilarating.monitoring.internet-measurement.com|7
192.42.116.178|26.tor-exit.nothingtohide.nl|7
185.220.101.188|tor-exit-188.relayon.org|7
45.161.176.1|45.161.176.1.serginetbandalarga.com.br|7
218.92.0.56|-|7
80.82.77.139|dojo.census.shodan.io|7
68.183.132.72|-|7
61.177.172.179|-|7
51.89.153.112|ns3145504.ip-51-89-153.eu|7
180.71.47.198|-|7
185.220.100.252|tor-exit-1.zbau.f3netze.de|7
103.251.167.20|-|7
80.253.31.232|-|7
80.67.167.81|nosoignons.cust.milkywan.net|7
167.94.145.60|-|7
175.207.13.22|-|7
42.200.78.78|42-200-78-78.static.imsbiz.com|7
220.85.247.129|-|7
212.70.149.150|-|7
118.193.16.50|-|7
198.235.24.173|-|7
192.42.116.198|8.tor-exit.nothingtohide.nl|7
199.45.154.49|scanner-203.hk2.censys-scanner.com|7
71.6.165.200|census12.shodan.io|7
207.90.244.6|-|7
167.94.138.33|scanner-06.ch1.censys-scanner.com|7
167.94.138.36|scanner-06.ch1.censys-scanner.com|7
167.94.138.35|scanner-06.ch1.censys-scanner.com|7
68.183.108.31|work.ameriinfo.com|7
66.240.219.146|burger.census.shodan.io|7
167.94.146.56|-|7
167.94.146.58|-|7
167.94.146.59|-|7
157.245.124.106|-|7
61.244.169.102|061244169102.ctinets.com|7
138.68.58.124|-|7
162.142.125.14|scanner-04.ch1.censys-scanner.com|7
162.142.125.13|scanner-04.ch1.censys-scanner.com|7
162.142.125.12|scanner-04.ch1.censys-scanner.com|7
162.142.125.11|scanner-04.ch1.censys-scanner.com|7
61.177.172.136|-|7
179.43.180.106|hostedby.privatelayer.com|7
50.225.176.238|-|7
218.92.0.29|-|7
218.92.0.22|-|7
218.92.0.24|-|7
218.92.0.27|-|7
185.191.126.213|-|7
71.6.167.142|census9.shodan.io|7
167.248.133.185|scanner-29.ch1.censys-scanner.com|7
167.248.133.184|scanner-29.ch1.censys-scanner.com|7
167.248.133.189|scanner-29.ch1.censys-scanner.com|7
167.248.133.188|scanner-29.ch1.censys-scanner.com|7
103.63.108.25|static.cmcti.vn|7
213.89.216.193|c213-89-216-193.bredband.tele2.se|7
222.102.214.75|-|7
125.99.173.162|-|7
209.97.186.17|-|7
222.186.160.114|-|7
165.227.87.78|-|7
222.168.30.19|-|7
162.142.125.214|scanner-05.ch1.censys-scanner.com|7
162.142.125.215|scanner-05.ch1.censys-scanner.com|7
162.142.125.216|scanner-05.ch1.censys-scanner.com|7
162.142.125.217|scanner-05.ch1.censys-scanner.com|7
175.204.36.249|-|7
218.156.128.226|-|7
210.212.99.168|static.ill.210.212.99.168/24.bsnl.in|7
207.90.244.14|-|7
220.80.223.144|-|7
218.92.0.112|-|7
218.92.0.113|-|7
218.92.0.118|-|7
198.57.248.56|wir.wirefeeds.com|7
71.6.158.166|ninja.census.shodan.io|7
167.94.145.54|-|7
221.156.105.215|-|7
167.248.133.34|scanner-08.ch1.censys-scanner.com|7
218.156.108.222|-|7
85.172.189.189|-|7
89.97.218.142|89-97-218-142.ip19.fastwebnet.it|7
5.145.16.69|69-16-145-5.dyn.cable.qlnet.ch|7
159.65.220.18|ulaportal.com|7
185.142.236.36|green.census.shodan.io|7
167.94.138.49|scanner-07.ch1.censys-scanner.com|7
167.94.138.51|scanner-07.ch1.censys-scanner.com|7
221.167.63.25|-|7
167.94.145.58|-|7
167.94.145.55|-|7
81.28.167.30|-|7
103.92.24.242|-|7
141.98.11.179|srv-141-98-11-179.serveroffer.net|7
