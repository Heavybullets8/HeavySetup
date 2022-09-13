# Command to Container Cron Job

## Purpose

This can be set on a cron job, or just on a one-off thing even. 

All it does is sends a command to the container

```bash
#!/bin/bash

# Application Name Here:
app_name='nextcloud'

# Container Name Here:
container='hpb'
# You may not need this, if that is the case, comment it out, Then delete the `--container "$container"` in the last line below, chances are you don't need it. 


# Command to Container/Pod here:
command='php occ files:scan --all'


# Note: if the command has single quotes in it, you will have
# to switch to double quotes and escape all the special characters between the double quotes
# More info here: https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_03.html


#ignored dependency pods, No change required
ignore="mariadb|redis|postgres|memcached|cron|coredns|nvidia|openebs"

namespace=$(k3s kubectl get namespaces | awk '{print $1}' | grep -i ^ix-"$app_name"$ || echo "Are you sure, you used the right app name?")

pod=$(k3s kubectl get -n "$namespace" pods | awk '{print $1}' | grep ^"$app_name" | grep -Ev "$ignore")

k3s kubectl exec -n "$namespace" --stdin --tty "$pod" --container "$container" -- $command

```

> This specific example will send the command `php occ files:scan --all` to Nextcloud's `hpb` container (which will then re-scan all of the files, adding them to the WEB-GUI if they are not already there)
>> Nextcloud REQUIRES that you specify the `hpb` container to run this command however

<br >

- Usually you don't need to specify the container, so you can delete `container='hpb` and `--container "$container"` if you do not need them..

    -  If you don't know if you need them.. you likely don't need them

