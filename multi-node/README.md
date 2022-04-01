# Deploy Wazuh Docker in multi node configuration

This deployment generates a Docker Compose stack with 2 Wazuh Manager container, 3 Wazuh Indexer container and 1 Wazuh Dashboard container.

For the next deployment, the following steps must be performed:

1) Increase max_map_count on your host (Linux)
```
$ sysctl -w vm.max_map_count=262144
```
    This command must be run with root permissions


2) Run the certificate creation script:
```
$ docker-compose -f generate-indexer-certs.yml run --rm generator
```
3) Start the stack with docker-compose:

    In Foregroud:
```
$ docker-compose up
```

    In Background:
```
$ docker-compose up -d
```


The stack takes about 1 minute to get up for the first time, since Wazuh Indexer must be started for the first time and the Indexes and Index Patterns must be generated.