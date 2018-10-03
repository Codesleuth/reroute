# reroute

## Setup

Clone this repo

```bash
git clone https://github.com/Codesleuth/vpn-fix-2
```

### Whitelist

Copy `whitelist.sample.txt` to `whitelist.txt` and add in IP addresses and/or hosts you want to access through the VPN **One per each line**.

e.g.

```
nearform.com
github.com
1.2.3.4
5.6.7.8
```

### Connect and Fix!

1. Connect to your VPN
2. Run the `vpn-fix` script and specify your prefered gateway and vpn interface
    ```bash
    sudo -E bash -c 'LOCAL_GATEWAY=192.168.1.254 VPN_INTERFACE=utun1 ./vpn-fix'
    ```

#### `LOCAL_GATEWAY`

Set this environment variable to the gateway IP you want to use. You can easily get this before connecting to the VPN and checking the IP listed with `netstat -nr | grep default`.

#### `VPN_INTERFACE`

Get the interface name of the VPN in use. This is likely to be `utun1` (the default). However, if this is not correct, connect to the VPN and look at the interface listed when running `netstat -nr | grep default` and you will see the interface listed at the end (e.g. `utun1`).

### Updating the Whitelist

You can also easily update your whitelist and and run again. The entries will be removed when you disconnect from the VPN so ensure you reconnect if you want to wipe out the list (or use `route del <ip>`).

Some particular sets of VPN software will nuke your route table when they disconnect, so be aware that you may have to run this again when you move between WiFi access points, or resume from sleep etc.

# License

MIT (see `LICENSE` file)

# Contributing

Please do open PRs.
