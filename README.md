# ghe_canary

This repository contains a Jenkinsfile suited for testing connectivity to a GitHub Enterprise deployment.  The sole parameter is `CLONE_URL`, which should be set to the URL of the repo to be cloned to test connectivity.  Last of all, Slack and the `slackSend` Jenkins plugin are required for this pipeline to operate.