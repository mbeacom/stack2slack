# Stack to Slack

This [Slack](https://slack.com/) bot monitors [StackExchange](https://stackexchange.com/) tags and automatically
publishes new questions in configured Slack channels.

It has been initially created to post all questions related to the [API Platform](https://api-platform.com) framework
in a dedicated channel of the Slack of [Les-Tilleuls.coop](https://les-tilleuls.coop) (the company behind the framework).

[![Go Report Card](https://goreportcard.com/badge/github.com/dunglas/stack2slack)](https://goreportcard.com/report/github.com/dunglas/stack2slack)
[![Build Status](https://travis-ci.org/dunglas/stack2slack.svg?branch=master)](https://travis-ci.org/dunglas/stack2slack)
[![Docker Automated build](https://img.shields.io/docker/automated/dunglas/stack2slack.svg)](https://hub.docker.com/r/dunglas/stack2slack/)

## Installing

1. [Register a new Slack bot](https://my.slack.com/services/new/bot) and grab the generated API token
2. [Download](https://github.com/dunglas/stack2slack/releases) and extract the binary corresponding to your platform
3. Start the daemon: `DEBUG=1 SLACK_API_TOKEN=<your-API-token> TAG_TO_CHANNEL='{"stackoverflow-tag": "slack-channel"}' ./stack2slack`
4. Finally, invite the bot in channels it will post: `/invite @bot-name`

Alternatively, you can use the official [Docker](https://www.docker.com/) image instead of downloading a binary: `docker run -e DEBUG=1 -e SLACK_API_TOKEN=<your-API-token> -e TAG_TO_CHANNEL='{"stackoverflow-tag": "slack-channel"}' dunglas/stack2slack`

If you use a [Kubernetes](https://kubernetes.io/) (e.g. a Google Container Engine cluster), you can install Stack 2 Slack
very easily with the [Helm](https://helm.sh/) package manager:

1. Clone this repository: `git clone git@github.com:dunglas/stack2slack.git`
2. Install the provided chart:

    helm install \
        --set slackApiToken=<slackApiToken> \
        --set tagToChannel.stackExchangeTag=slackChannel \
        ./chart/stack2slack

## Building from Sources

This bot is written in [Go](https://golang.org/) (golang), you need a proper install of it to compile the sources.

1. Clone this repository: `git clone https://github.com/dunglas/stack2slack.git`
2. Get the  dependencies `go get`
3. Compile the app: `go build`

## Credits

Written by [Kévin Dunglas](https://dunglas.fr).
Sponsored by [Les-Tilleuls.coop](https://les-tilleuls.coop).
