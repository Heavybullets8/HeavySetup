## Flag Table


| Flag 	| Example                	| Parameter       	| Description                                                                                                                                                                                                                	|
|------	|------------------------	|-----------------	|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| -U   	| -U <br>-U 5            	| None or Integer 	| Update applications, ignoring major version changes<br>_Optionally, you can supply a number after the argument to update multiple applications at once_                                                                    	|
| -u   	| -u<br>-u 5             	| None or Integer 	| Update applications, do NOT update if there was a major version change<br>_Optionally, you can supply a number after the argument to update multiple applications at once_                                                 	|
| -b   	| -b 14                  	| Integer         	| Backup `ix-appliactions` dataset<br>_Creates backups up to the number you've chosen_                                                                                                                                       	|
| -i   	| -i nextcloud -i sonarr 	| String          	| Applications listed will be ignored during updating<br>_List one application after another as shown in the example_                                                                                                        	|
| -r   	| -r                     	| None            	| Monitors applications after they update<br>If the app does not become "ACTIVE" after either:<br>The custom Timeout, or Default Timeout,<br>rollback the application.                                                       	|
| -v   	| -v                     	| None            	| Verbose Output<br>_Look at the bottom of this page for an example_                                                                                                                                                         	|
| -S   	| -S                     	| None            	| Shutdown the application prior to updating it                                                                                                                                                                              	|
| -t   	| -t 150                 	| Integer         	| Set a custom timeout to be used with either:<br>`-m` <br>_Time the script will wait for application to be "STOPPED"_<br>or<br>`-(u\|U)` <br>_Time the script will wait for application to be either "STOPPED" or "ACTIVE"_ 	|
| -s   	| -s                     	| None            	| Sync Catalogs prior to updating                                                                                                                                                                                            	|
| -p   	| -p                     	| None            	| Prune old/unused docker images                                                                                                                                                                                             	|

<br >
<br >

## Further Explanation

### Update Options

There are two options for updating

```
-U
```

This option does not care about major version changes, and will update even if there is one
> A major version change example:
>> `3.14.2` ---> `4.14.2` 

<br >

```
-u
```

This option will NOT update if there was a major version change
> `3.14.2` ---> `4.14.2` 
>> In this case, this application would NOT update, this is useful because a lot of the time, major version changes include breaking changes

<br >

#### Asynchronous Updates

Both of the update options have the ability to update multiple applications at one time

You can do this by placing a number after the `-u` or `-U`

Example:

```
-U 5
```

or

```
-u 5
```

- This will keep __up to __ 5 applications updating at one time
> You can place any whole number after the flag, except for 0

<br >

If you wish to NOT have multiple applications updating at once, simply use:

```
-u 1
```

or

```
-u
```
> If you do not place a number after `-u`, it will default to 1

<br >
<br >

### Backing Up

This does NOT backup individual applications (this is already taken care of when updating your app, a snapshot is taken, this is what allows you to rollback applications)

Instead, the script will back up your entire `ix-applications` dataset

> I will talk more about why this is useful in another section

<br >

You can backup your dataset prior to updating by:

```
-b 14
```
> You can use any whole number after `-b` besides 0

The number you choose is the __MAXIMUM__ number of `HeavyScript` backups that will be on your system
> It is important to not have this number be so high, if you have too many backups your system will slow down

<br >

Any number of backups that EXCEEDS the number you choose will be deleted
> If you started with 18 backups, and run `-b 14`, the 5 oldest backups will be deleted, because they exceed 14

<br >
<br >

### Ignoring

If you have an application that seems to break after every update, add it to the ignore list

Adding an application to the ignore list will completely ignore it when it comes to updating, neither `-u` or `-U` will update that application
> Just make sure you spell it right, capitalization does not matter however. 

<br >

Ignored applications MUST be added one by one

Example:

```
-i sonarr -i radarr -i nextcloud
```
> As you can see I am spacing out each `-i` away from each other
>> Using something like `-i sonarr radarr nextcloud` will NOT work, each app needs its own flag

_Note: The name you type after `-i` is the exact name YOU gave the application when creating it_

<br >
<br >

### Rolling Back

This is by far one of my favorite features, especially since a lot of the updates that have been pushed lately seem to fail, this has saved me a ton of time

```
-r
```

Will rollback an application to its previous version if it does not become active after your timeout

Example:
> Nextcloud is going from `3.1.14` to `3.1.15`, it fails to come back up for whatever reason, it will be rolled back to `3.1.14`

<br >
<br >

### Verbose

Sounds just as it is, it will produce more of an output when updating apps

<br >
<br >

### Shutdown Before Update

This will shutdown the individual application before it sends it the update command

Some people think this is a safer way to update applications, so I have it as an option, I personally don't use it

```
-S
```

Example:
> Jackett has an update, it is `active`, before updating Jackett the script will send it the shutdown command and wait for it to be fully `stopped` before continuing with the update


<br >
<br >

### Timeout

This is used in two places in the script

1. How long HeavyScript waits for the application to be `Active` before rolling it back
> If you are using `-r` anyway

2. How long HeavyScript waits for the application to Shutdown before it times out

<br >

Example:
```
-t 400
```
> Must use a whole number

> The number is in seconds

> If unset, the script uses 500 by default

<br >
<br >

### Sync

This just syncs the catalog prior to updating
> Syncing the catalog will ensure the latest application versions are being pulled down from the repository


<br >
<br >


### Prune

Prunes Old/Unused docker images
> If this is not done regularly, you can waste a lot of space with old images