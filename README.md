# Allow WiFi temporarily on Asuswrt-Merlin routers for kids

### How to use it.

It depends on `at` command. If `ipkg list_installed` does not list `at`, run `ipkg install at` to install it on root shell.

Copy the attached `reward.wifi` onto your Asus-Merlin router, give it the execute permission, and run it on root shell like:
```
# ./reward.wifi device_name 60
```
- The `device_name` is the name of a registered device with its mac address on your router. You may already have registered many devices for WiFi mac filtering or static IP allocation. You can specify more than one device name using like `"device1|device2"`, which is a regular expression actually.

- The `60` here means the time in minutes for which to allow WiFi, 25 if omitted.

### Run it and forget it.

It uses the `iptables` chain, `FORWARD`, and inserts a rule to the chain to allow WiFi for the specified device, and also registers an `at` job to delete the rule later at the specified time.

### Want to give it more time?

During a device is using WiFi, you can run the command again with more time specified and then you will get the expiration delayed by that amount of time.

### Further applications.

If you install `ssh` on your smartphone and set it up to run this command, ... ^^
