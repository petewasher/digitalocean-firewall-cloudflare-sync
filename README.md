# ![](https://cloud.digitalocean.com/favicon.png) Update DigitalOcean Firewalls with CloudFlare IPs

A little script to update **DigitalOcean** firewalls with right **CloudFlare** IPs.

This is useful to protect your backends against direct **DoS** and **DDoS** attacks on ports **80** and **443**.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/DigitalOcean_logo.svg/150px-DigitalOcean_logo.svg.png)
![](https://upload.wikimedia.org/wikipedia/en/6/65/Cloudflare_logo.png)

### Manual installation

 1) `git clone git@github.com:offensive-hub/cloudflare-update-firewall`
 2) `cd cloudflare-update-firewall`
 3) `sudo pip install -U -r requirements.txt`
 4) `cp .env.example .env && chmod 600 .env`
 5) Write right [Digital Ocean Access Token](https://www.digitalocean.com/docs/apis-clis/api/create-personal-access-token/) in file `.env`
 6) Execute `./update-firewall.py` to update DigitalOcean Firewalls

### Authors

* [Fabrizio Fubelli](https://fabrizio.fubelli.org)

### Thanks to

* [python-digitalocean](https://github.com/koalalorenzo/python-digitalocean)
