
## Downnloading and Installing Splunk
```terminal
wget -O splunk-10.4.1-5a009d941268-linux-amd64.deb "https://download.splunk.com/products/splunk/releases/10.4.1/linux/splunk-10.4.1-5a009d941268-linux-amd64.deb"

cd ~/Donwloads
```

```
# Download Splunk Enterprise
wget -O splunk-10.4.1-5a009d941268-linux-amd64.deb \
"https://download.splunk.com/products/splunk/releases/10.4.1/linux/splunk-10.4.1-5a009d941268-linux-amd64.deb"

# Install the package
sudo dpkg -i splunk-10.4.1-5a009d941268-linux-amd64.deb

# Start Splunk
sudo /opt/splunk/bin/splunk start

```

