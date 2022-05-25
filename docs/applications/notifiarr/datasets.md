## Config File

So, this isn't as easy as just taking screenshots.. 

You'll need to go to Notifiarrs site, and look at [their documentation](https://notifiarr.wiki/en/Client/Configuration) as well

Ensure the config file is named: 

```
notifiarr.conf
```

Luckily, the only thing you need to set FIRST is your User Interface password, we will configure the rest of the application with Environment Variables.



??? notifiarr "notifiarr.conf"
    ```
    ###############################################
    # Notifiarr Client Example Configuration File #
    # Created by Notifiarr v0.3.1   @ 222505T0022 #
    ###############################################

    ## Setting a UI password enables the human accessible web GUI. Must be at least 16 characters.
    ## The default username is admin; change it by setting ui_password to "username:password"
    ## Set to "webauth" to disable the login form and use only proxy authentication. See upstreams, below.
    ## Your proxy auth must pass x-webauth-user header if you set this to "webauth".
    ui_password = "username:password123456789"

    ```

<br />

## Dataset Permissions

After you have created your `notifiarr.conf` file, and filled out the required fields, you will need to create a dataset for the file to reside in

![!Networking: NZBGet](images/storage_permissions.png)

<br />