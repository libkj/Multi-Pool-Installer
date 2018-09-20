
# Ultimate Crypto-Server Setup Installer! 🚀

All in one installer for your crypto-server needs.

**Ultimate Crypto-Server Setup Installer!** Automates most of the tedious tasks of the following releases:

<img align="right" src="./.assets/install.gif?raw=true" height="215">

* YiiMP
* NOMP
* MPOS
* CryptoNote-Nodejs
* Generic faucet script


## 💾 Installation 

Installation:

Requires a fresh Ubuntu 16.04 installation.

```

```

## ▶️ Usage

If you try to run the installer as the root user, the installer will force you to create a user account and reboot in to it.

<p align="center">
  <img src="./.assets/naughty.png" alt="naughty"
       width="555" height="185">
</p>

After rebooting the server to your new user to start the installer type:
```
multipool
```

## ⚙️ YiiMP Single Server Install

The Yiimp Single Server Install is recommend for private or very small pools. It is recommended to have at least 4GB ram in order to function properly. 
Setup is automated after the following questions are answered:

Question | Default | Help
:--|:-:|:--
Are you using a sub-domain as the main domain | no | If you plan to use something like pool.example.com
Install SSL | yes | Installs a 90 day cert from LetsEncrypt
Domain Name | localhost | Change to your domain either example.com or pool.example.com
Stratum Domain | stratum.domain.name | This should be something other then your domain name
Support Email | support@domain.name | Used to send you system alerts
Your Public IP | pulls ip last used to acess web server | To verify go to http://www.whatsmyip.org
DB Root Password | autogenerated 36 character password | Default mysql root password
DB Panel User Password | autogenerated 36 character password | Default mysql frontend password
DB Stratum Password | autogenerated 36 character password | Default mysql stratum password
Admin Portal Access Location | AdminPortal | to access example.com/site/AdminPortal

Installation will take about 25 minutes to fully complete. You will get a message on the screen letting you know it has finished. 

#### A server reboot is REQUIRED after the installer is completed to finalize the installation process!

After rebooting the server log back in to your user account. And you will be greeted by the following screen:

<p align="center">
  <img src="./.assets/first_reboot.png" alt="first_reboot"
       width="771" height="635">
</p>

#### On first reboot it may take up to 1 minute before the cron screens auto-start. After waiting one minute type:
```
motd
```
and you should see this:

<p align="center">
  <img src="./.assets/running.png" alt="running"
       width="740" height="655">
</p>

#### To help make your server more secure we have changed the install locations and directory structure of YiiMP as follows:

Directory | Files
:--|:-:
/home/crypto-data/yiimp | General install location for YiiMP
/home/crypto-data/yiimp/starts | screens and stratum sh files - you do not need to run these
/home/crypto-data/yiimp/site | -
/home/crypto-data/yiimp/site/backup | backup location for mysql DB
/home/crypto-data/yiimp/site/configuration | New location of your serverconfig.php
/home/crypto-data/yiimp/site/crons | New location of the `main:blocks:loop2` sh files
/home/crypto-data/yiimp/site/log | New location for debug.log and your nginx server log
/home/crypto-data/yiimp/site/stratum | New location for your stratum files
/home/crypto-data/yiimp/site/web | New location for YiiMP web files

Permissions have been setup correctly allowing your main user write acess to the /home/crypto-data directories! Changing file or directory permissions after install will cause your YiiMP to not function correctly, you have been warned!!

By default even though all stratum algos start on server start, the ports have been blocked by the firewall. To open a port type:
```
sudo ufw allow port number
```

From there your YiiMP Single Server installation is fully completed. You can now go to example.com/site/AdminPortal to access your admin section and start adding your coins. 

#### 🔗 Commands

To view a screen type:
```
screen -r main|loop2|blocks|debug
```
To detach from a screen type:
```
ctrl+a+d
```
To start, stop or restart main|loop2|blocks|debug type:
```
screens start|stop|restart main|loop2|blocks|debug
```
We also suggest that you type:
```
yiimp
```
and get to know those commands as well!


## 🤖 YiiMP Multi-Server Install

The YiiMP Multi-Server Install is recommended for those that want to run larger public pools. This offers the most security and is a lot more complex on the setup. 

The following two tables show you the perfered server setup for the multi-server setup:

Role | OS Version | Recommended Ram
:--|:--|:-:
Web Server | Ubuntu 16.04 | 2GB
DB & Stratum Server | Ubuntu 16.04 | 4GB
Daemon Server | Ubuntu 16.04 only | 8GB+ 
 
 or 
 
Role | OS Version | Recommended Ram
:--|:--|:-:
Web Server | Ubuntu 16.04 | 2GB
DB Server | Ubuntu 16.04 | 2GB
Stratum Server | Ubuntu 16.04 | 2GB
Daemon Server | Ubuntu 16.04 only | 8GB+ 

It is also highly recommended to use a provider that offers private IP's between your servers. If your provider only offers public IP's you must install Wireguard (Installer provided). This will setup a secure VPN connection between your servers for the backend communication. 

#### If installing wireguard do not modify the default private IP's that are provide. Installation will fail!

Just like with the single server install there must be a user account created. If you attempt to run the script under root, it will force you to create a new user account and log in to it.

After the user accounts are created on each server setup <b>MUST</b> begin on the server that is hosting your database. You do not need to run the installer individually on each server.  

#### ✏️ During the setup process you will be prompted to enter the user name and password for each of your servers. This is required for the installer to be able to SSH in to each server to perform the installation tasks on that server. 


## 📦 NOMP Install

The NOMP options install everything you need to run NOMP and gets your first coin installed. It is recommended to have at least 4GB ram in order to function properly. 
Setup is automated after the following questions are answered:


## 🐣 MPOS Install

The MPOS options install everything you need to run MPOS and gets your first coin installed. It is recommended to have at least 4GB ram in order to function properly. 
Setup is automated after the following questions are answered:

## 🐛 CryptoNote-Nodejs Install

The CryptoNote-Nodejs options install everything you need to run CryptoNote-Nodejs and gets your first coin installed. It is recommended to have at least 4GB ram in order to function properly. 
Setup is automated after the following questions are answered:

## 📚 Generic faucet script

The faucet options install everything you need to run your own faucet script and setup multiple coins on it. Each coin will have their own sub-site. 
Setup is automated after the following questions are answered:

## ❤️ Credits

The following GitHubs have been a source of inspiration and code:

* [mailinabox](https://github.com/mail-in-a-box/mailinabox)
* [realeas-it](https://github.com/webpro/release-it)

The following forks have been used in the making of the script:

* [YiiMP](https://github.com/tpruvot/yiimp)
* [NiceNOMP](https://github.com/cryptosharks131/NiceNOMP)
* [UNOMP](https://github.com/UNOMP/unified-node-open-mining-portal)
* [cryptonote-nodejs](https://github.com/dvandal/cryptonote-nodejs-pool)
* [faucet script](https://github.com/ChristianGrieger/Cryptocurrency-faucet-script)

## 🎓 License

[MIT](http://webpro.mit-license.org/)

## 🎁 Support

Donations for continued support of this script are welcomed at:

* BTC 33XUK3hzZxmAPBgh2JMmMuVVSCAtpK9eQX
* BCH qp75x65svsuntmxze38sxqp47h4fqqgfyge5fgegah
* ETH 0xF2654882a26C3a226eEFF02E652D3aFFA1Bb682A
* LTC MTWpEuaLyj5AnvKxCKFh9fDbgsdNJgaECx
