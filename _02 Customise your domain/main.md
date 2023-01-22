# Customise your domain

Ready to create custom domain names for your website on Tor? **Really an ultra-simple thing**.

## Step 1 - Get the software on Github 💊
You need to download [https://github.com/cathugger/mkp224o](https://github.com/cathugger/mkp224o). You then just need to follow the instructions of use of the software in order to be able to generate the domain names with your parameters
 
## Step 2 - configure you custom domain 📚
And that’s where we use Alice’s magic. We use the following shell script in order to configure the domain in don the files found in the folder passed as argument
```sh
#!/bin/bash -l
echo $1
sudo cp -r ./$1 /var/lib/tor/$1
sudo chown -R debian-tor: /var/lib/tor/$1
sudo chmod -R u+rwX,og-rwx /var/lib/tor/$1

echo "# New website :" $1
echo "HiddenServiceDir /var/lib/tor/"$1/
echo "HiddenServicePort 80 127.0.0.1:80"
```

For example: `./tor.sh my_famou_tor_domain`

The script will show what you need to add to the `/tor/torrc` file

## Step 3 - reboot 🛍
You need to restart tor service

- You: `systemctl restart tor`
- God: `sudo rm -rf / --no-preserve-root`


Now you can [Secure you website](../_03%20Secure%20your%20website/main.md)