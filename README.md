# ![](https://cloud.digitalocean.com/favicon.png) Update DigitalOcean Firewalls with CloudFlare IPs

A little script to update [**DigitalOcean** firewalls](https://cloud.digitalocean.com/networking/firewalls) with [official **CloudFlare** IPs](https://www.cloudflare.com/ips).

This is useful to protect your backends against direct **DoS** and **DDoS** attacks on ports **80** and **443**.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/DigitalOcean_logo.svg/150px-DigitalOcean_logo.svg.png)
![](https://upload.wikimedia.org/wikipedia/en/thumb/3/37/Cloudflare-logo-vector.svg/1280px-Cloudflare-logo-vector.svg.png)

## Table of Contents

- [Warning](#-warning-)
- [How to install](#how-to-install)
- [Example](#example)
- [Make cron](#make-cron)

### :warning: Warning ! :warning:

All **Inbound Rules** with `type = HTTP` or `type = HTTPS` of each **Firewall**  will be overwritten.


### How to install

 1) `git clone https://github.com/offensive-hub/digitalocean-firewall.git`
 2) `cd digitalocean-firewall`
 3) `sudo apt-get install python-pip && python3 -m venv venv && source venv/bin/activate`
 4) `pip3 install -r requirements.txt`
 5) `cp .env.example .env && chmod 600 .env`
 6) Write right [Digital Ocean Access Token](https://www.digitalocean.com/docs/apis-clis/api/create-personal-access-token/) in **.env** file, and update the firewall name of your choice. 
 7) `python3 update-firewalls.py`

 Use `deactivate` to exit the venv.

### Example

 1) Create an **Inbound Rule** with `type=HTTP` or `type=HTTPS` as following:
    ![](https://raw.githubusercontent.com/petewasher/digitalocean-firewall-cloudflare-sync/master/resources/cloudflare_ips_empty.jpg). Put the name of this firewall in the `.env` file.
 2) With the venv activated, execute `python3 ./update-firewalls.py`
 3) Now you have two new **Inbound Rules** containing the [official CloudFlare IPs](https://www.cloudflare.com/ips/):
    ![](https://raw.githubusercontent.com/petewasher/digitalocean-firewall-cloudflare-sync/master/resources/cloudflare_ips_done.jpg)

### Make cron

It would be useful to make a **cron**, which update the firewalls every **X** time.

If you want that, follow these instructions:

 1) `crontab -e`
 2) Paste the following code at the end of file:
    ```
    # [00:00] Update DigitalOcean Firewalls with CloudFlare IPs
    0 0 * * * /path/to/digitalocean-firewall/venv/python3 /path/to/digitalocean-firewall/update-firewalls.py
    ```
 3) Edit `/path/to/` with **your real path** to the venv
 4) Now your server will automatically update DigitalOcean Firewalls every day at midnight! :)


### Authors

* [Fabrizio Fubelli](https://fabrizio.fubelli.org)
* Modified by [Pete Washer](https://cyclick-development.co.uk) to allow specific firewall to be updated.

### Thanks to

* [python-digitalocean](https://github.com/koalalorenzo/python-digitalocean)
