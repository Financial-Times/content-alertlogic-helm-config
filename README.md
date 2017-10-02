## alert-logic

## Introduction

Alert Logic agent runs as a daemonset in k8s cluster.

## Set up instructions

* Docker image for alert logic is in nexus (courtesy Membership)

* Create a secret to hold the nexus credentials. The credentials will be used to pull the alert logic docker image from the nexus repository. Password is stored in Lastpass (For upp: `upp-docker`. For pac: `pac-docker`)

    `kubectl create secret docker-registry nexusregistry --docker-server=nexus.in.ft.com:5000 --docker-username=<nexus_username_for_upp/pac> --docker-password=<password_from_lastpass> --docker-email=universal.publishing.platform@ft.com`

* Alert logic registration key should be stored as a secret in the cluster. Alert logic registration key is stored in LastPass (`AlertLogic Setup`)

    `kubectl create secret generic alertlogicsecret --from-literal=registration-key=<key_from_lastpass>`

* Threat manager host ip address can be passed in the global config. Please look at the `AlertLogic Setup` Last pass note to get the IP address corresponding to the environment and region.
