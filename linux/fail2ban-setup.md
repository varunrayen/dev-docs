# Fail2Ban Setup

First, we need to update our local package index and then we can use `apt` to download and install the package:



```text
sudo apt-get update
sudo apt-get install fail2ban
```

### Configure Fail2Ban with your Service Settings <a id="configure-fail2ban-with-your-service-settings"></a>

The fail2ban service keeps its configuration files in the `/etc/fail2ban` directory. There is a file with defaults called `jail.conf`.

Since this file can be modified by package upgrades, we should not edit this file in-place, but rather copy it so that we can make our changes safely. In order for these two files to operate together successfully, it is best to only include the settings you wish to override in the `jail.local` file. All default options will be taken from the `jail.conf` file.

Even though we should only include deviations from the default in the `jail.local` file, it is easier to create a `jail.local` file based on the existing `jail.conf` file. So we will copy over that file, with the contents commented out, as the basis for the `jail.local` file. You can do this by typing:

```text
awk '{ printf "# "; print; }' /etc/fail2ban/jail.conf | sudo tee /etc/fail2ban/jail.local
```

Once the file is copied, we can open the original `jail.conf` file to see how things are set up by default

```text
sudo nano /etc/fail2ban/jail.conf
```

### **Settings to be configured**

```text
### jail.conf ###


[DEFAULT]

ignoreip = 127.0.0.1/8
bantime = 600
findtime = 600
maxretry = 3
```

**`ignoreip:`** This setting configures the source addresses that fail2ban ignores. By default, it is configured to not ban any traffic coming from the local machine. You could add additional addresses to ignore by adding a `[DEFAULT]` section with an `ignoreip` setting under it to the `jail.local` file. You can add additional addresses by appending them to the end of the directive, separated by a space.

**`bantime:`**parameter sets length of time that a client will be banned when they have failed to authenticate correctly. This is measured in seconds. By default, this is set to 600 seconds, or 10 minutes.

**`findtime & maxretry:`**

The `maxretry` variable sets the number of tries a client has to authenticate within a window of time defined by `findtime`, before being banned. With the default settings, the fail2ban service will ban a client that unsuccessfully attempts to log in 3 times within a 10 minute window.



```text
sudo service fail2ban start
```

