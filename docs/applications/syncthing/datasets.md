This is another application I had to leave wide-open to get to work properly. 

For some reason, using the regular permissions settings would result in permissions errors off and on, it was incredibly annoying.

So, as you can see I created a `POSIX ACL` and set all of the users to `apps` and I gave `other` full permissions as well.

Unsafe I know, but I really could not find another way to get this working.

??? Note "Note"
    The `apps`:`apps` user:group is built into Truenas SCALE, it is the default user for most applications on Truenas SCALE. You do not have to create a separate user for each application.

    When configuring your application you'll typically see user:group `568`, this is the UID for `apps` and its recommended not to change it.

![!Dataset: syncthing](images/dataset.png)