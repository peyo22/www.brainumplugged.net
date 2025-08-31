+++
date = '2021-04-14T09:00:00+02:00'
draft = false
title = 'CentOS7 yum - Remove subscription-Manager nag'
author = "Peyo"
showToc = false
hidemeta = false
comments = false
description = "CentOS 7 gives a nag about the subscription-manager when using yum. If you're annoyed by that, here's how to remove it."
categories = ["Linux", "CentOS", "Sysadmin", "Cheatsheet"]
tags = ["shell"]
+++
## The nag message
```
root@vm$ yum makecache
Loaded plugins: fastestmirror, langpacks, post-transaction-actions, product-id, search-disabled-repos,
              : subscription-manager, versionlock

This system is not registered with an entitlement server. You can use subscription-manager to register.

Loading mirror speeds from cached hostfile
```

Basically it is telling you your system is not enrolled to Red Hat Subscription Management.  

## The fix
To remove the nag, you just have to disable the subscription-management (yum) plugin.  
The config file is `/etc/yum/pluginconf.d/subscription-manager.conf`.  

As root:
```shell
sed -i 's/enabled=.*$/enabled=0/' /etc/yum/pluginconf.d/subscription-manager.conf
```
