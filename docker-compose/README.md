#### Setup
Place `docker-compose.yml` and external-adapters repo in the same directory
```
mkdir CHAINLINKmain_compose
cd CHAINLINKmain_compose
git clone https://github.com/smartcontractkit/external-adapters-js
# copy paste contents and edit user_uid, ports, tokens
nano docker-compose.yml
```

#### Start service
`docker-compose up --force-recreate --build -d`

#### Stop service
`docker-compose down`

#### Watch logs
`docker-compose logs --follow`  
`docker logs cln_node --follow`

#### Check status
```bash
chainlinkuser@server> docker-compose ps
      Name                     Command               State           Ports
-----------------------------------------------------------------------------------
cln_amberdata       docker-entrypoint.sh yarn  ...   Up      0.0.0.0:8042->8080/tcp
cln_coingecko       docker-entrypoint.sh yarn  ...   Up      0.0.0.0:8041->8080/tcp
cln_coinlore        docker-entrypoint.sh yarn  ...   Up      0.0.0.0:8044->8080/tcp
cln_coinpaprika     docker-entrypoint.sh yarn  ...   Up      0.0.0.0:8043->8080/tcp
cln_cryptocompare   docker-entrypoint.sh yarn  ...   Up      0.0.0.0:8040->8080/tcp
cln_node            chainlink local n -p /chai ...   Up      0.0.0.0:6688->6688/tcp
```


#### *Notice* We get UID for running bridges (username didn't work) and set it in yml in `user` field:

```bash
chainlinkuser@server> lslogins -u
 UID USER      PROC PWD-LOCK PWD-DENY LAST-LOGIN GECOS
   0 root       163                              root
...
1020 chainlink   32                              ,,,
```


#### You may need to install latest docker-compose version

See: https://docs.docker.com/compose/install/
