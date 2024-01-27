
# How to Set Up Tor for Linux (In This Method We Fix DNS TimeOut Error)

**Step 1: Install Necessary Libraries**

```bash
sudo apt install tor proxychains
```

**Step 2: Start and Enable Tor Services**

```bash
sudo systemctl enable tor
```

**Step 3: Configure Proxychains Routing**

Open the proxychains configuration file:

```bash
vim /etc/proxychains.conf
```

Edit the file to include the following lines:

```conf
# defaults set to "tor"
socks5  127.0.0.1 9050
```

Save and exit the file.

**Step 4: Change Proxychains Default DNS**

Open the proxychains DNS resolver file:

```bash
vim /usr/lib/proxychains3/proxyresolv
```

Change the line:

```conf
${PROXYRESOLV_DNS:-4.2.2.2}
```

to:

```conf
${PROXYRESOLV_DNS:-1.1.1.1}
```

Save and exit the file.

**Step 5: Test Your Proxy**

Test your proxy connection by pinging YouTube:

```bash
proxychains ping youtube.com
```

If the ping command succeeds, you have successfully configured Tor and proxychains.
