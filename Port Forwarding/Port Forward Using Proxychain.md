Use ssh to forward request to target via ssh
```
ssh -N -D 0.0.0.0:1083 database_admin@10.4.250.215
```
![45201694646e696bae6ffd713ec62c9b.png](./images/45201694646e696bae6ffd713ec62c9b.png)

Setup proxychain conf
![b758deed09a44dce07b5a1bc9ff6d157.png](./images/b758deed09a44dce07b5a1bc9ff6d157.png)

After that, simply use the command that we want (e.g, nmap)
```
proxychains -q nmap 172.16.1.5 -d -sV -T4 -Pn -oN=scan.txt (change the command to your liking)
```
![ecaba39e8bab2912b9e8197592cb6b12.png](./images/ecaba39e8bab2912b9e8197592cb6b12.png)

Alternative command to port scanning without nmap
```
for port in {4800..4900}; do proxychains nc -zv -w1 172.16.250.217 $port 2>&1 | grep OK; done
```
![40b9b2526f8ffcd70fa2c978a693a289.png](./images/40b9b2526f8ffcd70fa2c978a693a289.png)