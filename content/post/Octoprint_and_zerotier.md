---
title: "Octoprint and Zerotier"
date: 2020-01-28T20:34:07Z
draft: false
---

This post contains detailed instructions on how to set up zerotier on your octoprint instance on a raspberry pi.


1. Install the required dependencies on the OctoPi:
```
sudo apt install curl gnupg2
```
2. If you trust zerotier, copy the following command and paste it into your terminal:
```
curl -s 'https://raw.githubusercontent.com/zerotier/ZeroTierOne/master/doc/contact%40zerotier.com.gpg' | gpg --import && \
if z=$(curl -s 'https://install.zerotier.com/' | gpg); then echo "$z" | sudo bash; fi
```
3. Wait for it to complete.
![Zerotier Install](/images/gif/zerotier.gif)

4. Go to https://zerotier.com and sign up with your preferred method available.
5. Create a network, make sure you do not overlap with the local network you are using (if 192.168.0.X, use 172.23.X.X).
For examples, see: https://zerotier.atlassian.net/wiki/spaces/SD/pages/8454145/Getting+Started+with+ZeroTier
6. Issue the following command to join your Octopi to the network:
```
sudo zerotier-cli join <NETWORK_ID>
```
7. Go to the zerotier control panel, enter the network you just created and scroll down until you can authenticate the access for the new
connection from the octopi.
8. Add Zerotier to your desired devices and join them to the same network. 
![Creating and joining network](/images/gif/capture.gif)

And with that you should be able to securely access your Octoprint setup when you are outside of your home.

More information can be found on the following page:
https://zerotier.atlassian.net/wiki/spaces/SD/overview

