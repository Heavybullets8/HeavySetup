# Command to Container Cron Job

## Purpose

This can be set on a cron job, or just on a one-off thing even. 

All it does is sends a command to the container

```bash
#!/bin/bash
set -e

# Variables: Please fill these out before running the script.

# app_name: The name of the application you are targeting.
# Example: "nextcloud"
app_name="nextcloud"

# container: The specific container within the pod you are targeting.
# Leave this blank if you want to target the pod itself.
# Example: "web-server"
container="hpb"

# command: The command you want to run inside the container or pod.
# NOTE: If the command includes special characters, you will need to escape them.
# Example: "ls -la" or "echo \"Hello, World!\""
command="php occ files:scan --all"

# ignore: A pipe-separated list of pod or container names to ignore.
# These names will be excluded from the selection of target pods.
# Example: "mariadb|redis|postgres"
ignore="mariadb|redis|postgres|memcached|cron|coredns|nvidia|openebs|cnpg"

# Functions (No changes needed below this line)
get_namespace() {
    k3s kubectl get namespaces | awk '{print $1}' | grep -i ^ix-"$1" || echo "Are you sure, you used the right app name?" >&2
}

get_pod() {
    k3s kubectl get -n "$1" pods --field-selector=status.phase=Running --no-headers | awk '{print $1}' | grep -oE ^"$2-[[:alnum:]]{9,10}-[[:alnum:]]{5}" | grep -iEv "$3" | head -n 1
}

check_container() {
    [ -n "$1" ] && k3s kubectl get -n "$2" pod "$3" -o=jsonpath="{.spec.containers[*].name}" | grep -w "$1" || echo ""
}

# Main script
namespace=$(get_namespace "$app_name")

if [ -z "$namespace" ]; then
    echo "Namespace for the app not found. Exiting." >&2
    exit 1
fi

pod=$(get_pod "$namespace" "$app_name" "$ignore")

if [ -z "$pod" ]; then
    echo "Pod for the app not found. Exiting." >&2
    exit 1
fi

container_exists=$(check_container "$container" "$namespace" "$pod")

if [ -n "$container_exists" ]; then
    k3s kubectl exec -n "$namespace" "$pod" --container "$container" -- $command
else
    k3s kubectl exec -n "$namespace" "$pod" -- $command
fi
```

> This specific example will send the command `php occ files:scan --all` to Nextcloud's `hpb` container (which will then re-scan all of the files, adding them to the WEB-GUI if they are not already there)
>> Nextcloud REQUIRES that you specify the `hpb` container to run this command however

<br >

- Usually you don't need to specify the container, so you can delete `container='hpb` and `--container "$container"` if you do not need them..

    -  If you don't know if you need them.. you likely don't need them

