# Allow WiFi temporarily on Asuswrt-Merlin routers for kids

### How to use it.

It depends on `at` command. If `ipkg list_installed` does not list `at`, run `ipkg install at` to install it on root shell.

Copy the attached `reward.wifi` onto your Asus-Merlin router, give it an execute permission, and run it on root shell like:
```
# ./reward.wifi device-name 60
```
- The `device-name` is the name of a registered device with its mac address on your router. You may already have registered many devices for WiFi filtering or static IP allocation.

- The `60` here means the time in minutes for which to allow WiFi, 25 if omitted.

### Run it and forget it.

It uses the `iptables` chain, `FORWARD`, and inserts a rule to the chain to allow WiFi for the specified device, and also registers an `at` job to delete the rule later at the specified time.

### Want to give it more time? No problem.

During a device is using WiFi, you can run the command again with more time specified and then you will delay the expiration time by that amount of time.
