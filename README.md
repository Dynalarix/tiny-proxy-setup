Hardware requirements: 1 cpu 1Gb ram 10Gb rom
After installing you need to edit /etc/tinyproxy/tinyproxy.conf:

1. Change the Port (Optional)
Allow Connections By default (default is 127.0.0.1 - localhost)
find 'allow' lines to add your ip. to allow all ip simply comment all 'Allow' sections !(dangerous without BasicAuth)!

2. Authentication: To prevent strangers from usin your proxy, look for the BasicAuth option inside tineproxy.conf and add a username and password:
```
BasicAuth username your-password
```

3. Restart and Enable the Service with: 
```
sudo systemctl restart tinyproxy
sudo systemctl enable tinyproxy
```

4. Secure and Test Your Proxy
```
sudo ufw allow 8888/tcp
export http_proxy="http://username:your-password@vps-ip:port"
curl ifconfig.me;echo
```

Test on Client Device: On your local computer, go to your network or browser proxy settings, enter your VPS IP address and the port (e.g., 8888) and visit an ip checker site to confirm your traffic is routing through the VPS. Enjoy.

Logs in real time: 
```
sudo tail -f /var/log/tinyproxy/tinyproxy.log
```
