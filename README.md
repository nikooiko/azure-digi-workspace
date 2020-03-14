# azure-digi-workspace

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
