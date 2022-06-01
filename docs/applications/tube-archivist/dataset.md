**This is the location your videos will be stored, you can skip this step if you are fine with just using PVC instead**

As you can see I created a dataset in `media`, since this is media after all.

Unfortunately, I could not find a way to run this application without using 777.. 

But as you can see I left the permissions wide open, and set the user:group to `apps`

??? Note "Note"
    The `apps`:`apps` user:group is built into Truenas SCALE, it is the default user for most applications on Truenas SCALE. You do not have to create a separate user for each application.

    When configuring your application you'll typically see user:group `568`, this is the UID for `apps` and its recommended not to change it.

![!Dataset: Tube](images/dataset.png)