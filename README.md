
# Pi-Hole for blocking unwanted ads at the network level 

Ads support the majority of the free applications and websites that we like to use on a regular basis. But certain advertisements can be intrusive and even obtrusive. This is why a lot of users choose adblocking plugins that are browser-based.

Pi-Hole is a programme designed to prevent advertisements on the network. It serves as a Domain Name Service (DNS) server, querying all domains attempting to reach networked devices and blocking those that deliver advertisements.

As a result, advertisements won't be downloaded or shown on the gadgets linked to your home network.

One of the greatest ad-blocking alternatives is Pi-Hole. Another name for it is the internet ad sinkhole.




## Setting up DNS Server for Raspberry Pi

You have to set up the DNS server for your Raspberry Pi. 

Every website has a domain, but this is only for the convenience of human users. On the machine level, the domain is identified by several digits on the internet registry, known as an IP address.

A DNS server is like a phonebook, it stores the corresponding IP address for every URL.

So, every time you want to connect to a site, you send a query to the DNS server.

Your device then sends a request to that IP address, and then loads the site.

This should be the end of the process, but most of the time, it never is.

Your computer gets a request to load additional resources to fill the page, some of which include ads.

Here’s where pi-hole comes in. It keeps a library of all the misleading requests, and “sinks” them all to non-resolveable IPs.

As a result, the site won’t load. You’ll see blank spaces on the parts of the page that would have had an advert.

For this , we install DNS software on our rpi4
```
sudo apt install dnsmasq
```
After installation , we configure the  dnsmasq.conf file
```
sudo nano /etc/dnsmasq.conf
```
Locate and uncomment the following lines by removing the hash sign (#)

1.domain-needed 

2.bogus-priv

3.no-resolv

Locate and remove the following line
```#sever=/localnet/192.168.0.1```

Replace it with 
```
server=8.8.8.8

server=8.8.4.4 
```


Locate the cache size and change it to 1000
``` cache-size=1000 ```

Exit the configuration file, save the file.

Restart DNSMasq to apply the changes
```
sudo systemctl restart dnsmasq
```
Check the status of the DNS server
```
sudo systemctl status dnsmasq
```


## Installation

Install Pi-Hole with the below command on your terminal

```bash
curl -sSL https://install.pi-hole.net | bash
```
You will need to set up the DNS server and assign static ip address to your rpi,so your router doesnt face any further issues.


After downloading Pi-Hole, it will open a new installation window

Select OpenDNS as your upstream DNS provider.

Click on Ok till you conclude the installation; if you feel you would like to change some settings, you can do it on the web portal as well.

After proper installation, you will be given a password, keep a note of it.





## Accessing the Web Portal 
Open a web browser and go to ```http://IP_ADDRESS/admin```, where IP_ADDRESS is the IPv4 address of your Pi-hole device . Click on log-in and enter your password. You should now be in the Pi-hole admin panel.


## Screenshots

![Pi-Hole Admin Web Portal]([[https://via.placeholder.com/468x300?text=App+Screenshot+Here](https://github.com/rebek-007/pihole/blob/master/admin.png)https://github.com/rebek-007/pihole/blob/master/admin.png](https://github.com/rebek-007/pihole/blob/master/admin.png)https://github.com/rebek-007/pihole/blob/master/admin.png)

