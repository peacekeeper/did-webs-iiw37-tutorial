# did:webs IIW Walkthrough

## Run Docker containers with keripy and dkr

```
docker compose down
docker compose up -d
docker compose exec dkr /bin/bash
```

## Create salt (seed) for AID private keys

```
kli salt
```

Example response:

```
0AAQmsjh-C7kAJZQEzdrzwB7
```

## Create AID

Note: Replace with your actual salt

```
kli init --name controller --salt 0AAQmsjh-C7kAJZQEzdrzwB7 --nopasscode --config-dir "./my-scripts" --config-file my-config
kli incept --name controller --alias controller --file "./my-scripts/my-incept.json"
```

Example AID:

```
EKYGGh-FtAphGmSZbsuBs_t4qpsjYJ2ZqvMKluq9OxmP
```

## (Optional) Perform more KERI operations

Optionally use `kli` to perform additional KERI operations such as key rotation, threshold signatures, etc., see KERI docs for details.

## (Optional) Resolve AID as did:keri

Optionally resolve the AID locally as did:keri, using an OOBI as resolution option.

Note: Replace with your actual AID

```
dkr did keri resolve --name controller --did did:keri:EKYGGh-FtAphGmSZbsuBs_t4qpsjYJ2ZqvMKluq9OxmP --oobi http://witnesshost:5642/oobi/EKYGGh-FtAphGmSZbsuBs_t4qpsjYJ2ZqvMKluq9OxmP/witness/BBilc4-L3tFUnfM_wJr4S4OJanAv_VmF_dJNN6vkf2Ha
```

## Decide your web address for did:webs

Find a web address (domain, optional port, optional path) that you control.

Example web address:

```
mydomain.com
```

## Generate did:webs files for AID

Note: Replace with your actual web address and AID

```
dkr did webs generate --name controller --did did:webs:mydomain.com:EPaP4GgZsB6Ww-SeSO2gwNDMNpC7-DN51X5AqiJFWkw6 --oobi http://localhost:5642/oobi/EPaP4GgZsB6Ww-SeSO2gwNDMNpC7-DN51X5AqiJFWkw6/witness/BBilc4-L3tFUnfM_wJr4S4OJanAv_VmF_dJNN6vkf2Ha
```
