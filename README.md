# cfddns

These scripts implement a portion of cloudflare's DNS records API
in python3.  The original goal was to make a very flexible implementation for use as a personal DynDNS tool compatible with privately held domains, so as to avoid blacklisting or exposure.

#### NOTE:  THERE IS VERY LITTLE SANITY CHECKING OR EXCEPTION HANDLING STILL.


### Getting Started:

Things you need:
* A domain name you own
* Access to the cloudflare account (free tier is fine) for that domain
* Your domain must have its SOA (start of authority) correctly assigned to CloudFlare
* Credentials:
    * zone ID of the domain
    * cloudflare API Token with DNS Edit privs for your zone
* A URL you trust to correctly return your WAN IP.  Ideally, you control it.  Some public options:
    * http://ifconfig.me/ip
    * https://api.ipify.org/?format=text
    * https://ip.seeip.org
    * http://myexternalip.com/raw


### Getting Started:

1) Sync the repo (duh)
2) Edit sample.conf appropriately and save as your own config filename in your favorite JSON editor. Config file Notes:

    a) The configuration file interval value is in seconds.  Some useful values: (600 = 10 minutes, 1800 = 30 minutes, etc)

    b) interface name doesn't matter (yet) as it's not fully implemented.
3) ```chmod u+x ./cfddns.py```
4) Please be mindful of hammering the API endpoints and/or ip checking servers when configuring the run interval.  I imagine a single check every 30 minutes is plenty-fast for most people.
5) ### NOTE: the configuration file will store your API credentials.  Protect it as a private key or password.

### TODO:
* iptables helper script and config entries
    * iptables fw rule number for delete + re-insert
    * iptables rule template


