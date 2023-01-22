# Create Tor website 🪄

If you don’t know what Tor network is starts by questioning your little life, and it’s surely that this documentation is absolutely not for you !

## Step 0 - the beginning 🧃
This step is relatively simple. You have to get up from your desk, go to the nearest store, get yourself a bottle of original flavor ice tea. Then against all odds, come home and fuck yourself in front of your computer, and read this documentation CAREFULLY.

## Step 1 - update upgrade
First, we need to update your system. It’s useless but it’s a cool thing to show you that you have to start typing on your ssh terminal from your server and that you are root. So you guys are admin hotties

```sh
sudo apt update
sudo apt upgrade
```

> what is the magic word? sudo

## Step 2 - install tor
It is also a fairly simple step, you just have to install the tor package available on all linux systems.

```
sudo apt install tor
```

## Step 3 - a little bit config
Now an ultra hard step to do: you must edit the following file: 
```
/etc/tor/torrc
```

Gods will show you the *vim* command, but Satan will ask you to open this file with a good *nano* as at the time 

You have to scroll a can to find the following commented lines: 
```
#HiddenServiceDir /var/lib/tor/hidden_service/
#HiddenServicePort 80 127.0.0.1:80

#HiddenServiceDir /var/lib/tor/other_hidden_service/
#HiddenServicePort 80 127.0.0.1:80
#HiddenServicePort 22 127.0.0.1:22
```
As you can see, tor can be configured to be used by multiple services on the same server. You would be able to host several services in the same place

You must therefore create at least 2 lines in the configuration files as on the "examples" in comment, which would give us in our case: 

```
HiddenServiceDir /var/lib/tor/i_love_potato/
HiddenServicePort 80 127.0.0.1:80

#HiddenServiceDir /var/lib/tor/hidden_service/
#HiddenServicePort 80 127.0.0.1:80
[...]
```

## Step 4 - welcome in the free world
In order to take into account the changes, simply use the following command in order to restart the Tor service so that it takes into account the updates

```
systemctl restart tor
```

And, and, and guess what? Your tor website is already online! 

In order to know what is the domain name, I propose you the following command in order to recover it, it is up to you to adapt it in your case

```
cat /var/lib/tor/hidden_service/hostname
```

## Step 5 - a perfect world
From now on, the service acts as a normal website. it’s up to you to configure your best request controller, such as apache2, nginx, caddy, httpd, in order to manage the destination website

As part of the test, I propose you a small website in the `website` folder so that you can test with a static site that does not promote any brand

## Step 6 - and what’s next ?
tor it’s funny but you want one more? click on [this nice link absolutely not doubted](../_02%20Customise%20your%20domain/main.md)

If you stop now, I’ll show you my head live: 

![](../.github/_01_1.gif)

> oh ! that suck