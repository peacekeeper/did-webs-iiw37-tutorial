# did:webs IIW37 Demo

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
kli init --name controller --salt 0AAQmsjh-C7kAJZQEzdrzwB7 --nopasscode --config-dir "/keripy/my-scripts" --config-file my-config
kli incept --name controller --alias controller --file "/keripy/my-scripts/my-incept.json"
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
https://peacekeeper.github.io/did-webs-iiw-demo/
```

## Generate did:webs files for AID

Note: Replace with your actual web address and AID, convert to did:web(s) conformant identifier

```
dkr did webs generate --name controller --did did:webs:peacekeeper.github.io:did-webs-iiw-demo:EKYGGh-FtAphGmSZbsuBs_t4qpsjYJ2ZqvMKluq9OxmP --oobi http://witnesshost:5642/oobi/EKYGGh-FtAphGmSZbsuBs_t4qpsjYJ2ZqvMKluq9OxmP/witness/BBilc4-L3tFUnfM_wJr4S4OJanAv_VmF_dJNN6vkf2Ha
```
