# Dnsmasq setup for Mac local development

Dnsmasq setup for my local development

## 1. Install

Install dnsmasq via Homebrew

```
$ brew install dnsmasq
```

## Configuration

Homebrew will create a configuration file for you.

Open file: 
```
$ sudo vim /usr/local/etc/dnsmasq.conf
```

Edit the file by adding the new line under the address. "test" represents the tld name. IP address is IP of the target. So *.test will route to 192.168.30.10.

```bash
address=/test/192.168.30.10
listen-address=127.0.0.1
```

## Start a service

Let Homebrew handle starting this service

```
$ sudo brew services start dnsmasq
```

After each change of configuration you need to restart dnsmasq service

```
$ sudo brew services restart dnsmasq
```

## Register resolver

You need to add resolver for `*.test` domain
```
$ sudo mkdir /etc/resolver
$ sudo touch /etc/resolver/test
```

Edit `/etc/resolver/test/` and add following line of code

```
nameserver 127.0.0.1
```

## Restart

After customizing resolving options you need to **RESTART YOU COMPUTER**
