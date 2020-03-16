# azure-digi-workspace

## Project Status
Currently the built images have all iotedge tools integrated, but there are many TODOs:
 - When the system uses **sysvinit** instead of **systemd** (case of ccimx6ulsbc) the init script malfunctions because it expects it to be debian based (e.g. expects /lib/init/vars.sh but files are missing).
 - The firmware currently contains the default iotedge/config.yaml which is now manually edited at runtime. To resolve it we can create a boot procedure that edits this at first boot. NOTE: that the config file is read-only by default.
 - By default the iotedge/config.yaml uses systemd based URIs for listen operations. On sysvinit systems this causes a malfunction at the daemon operation which prevents it from running. Temporarily the URIs are manually replaced with unix based URIs but need investigation to be configured correctly:
    ```yaml
        ...
        listen:
            management_uri: "unix:///var/run/iotedge/dmgmt.sock"
            workload_uri: "unix:///var/run/iotedge/dworkload.sock"
        ...
    ```


## Prerequisites
- Docker

## Instructions

Steps to build firmware for **ccimx6ulsbc**:
- `source ./setup-environment`
- `build-interractive` (host env)
- `build-ccimx6ulsbc` (builder env)

NOTE: `build-help` to see all available build commands (supports host and builder)

## Project Structure
- **builder**: The docker-based builder files
- **scripts**: Contains all the host scripts that are executed at the host environment.

## Related Repositories
- https://github.com/nikooiko/azure-digi-manifest
- https://github.com/nikooiko/dey-base
