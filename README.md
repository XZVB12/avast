# malice-avast

[![Circle CI](https://circleci.com/gh/malice-plugins/avast.png?style=shield)](https://circleci.com/gh/malice-plugins/avast) [![License](http://img.shields.io/:license-mit-blue.svg)](http://doge.mit-license.org) [![Docker Stars](https://img.shields.io/docker/stars/malice/avast.svg)](https://store.docker.com/community/images/malice/avast) [![Docker Pulls](https://img.shields.io/docker/pulls/malice/avast.svg)](https://store.docker.com/community/images/malice/avast) [![Docker Image](https://img.shields.io/badge/docker%20image-550MB-blue.svg)](https://store.docker.com/community/images/malice/avast)

Malice Avast AntiVirus

> This repository contains a **Dockerfile** of [avast](https://www.avast.com/en-us/linux-server-antivirus) for [Docker](https://www.docker.com/)'s [trusted build](https://store.docker.com/community/images/malice/avast) published to the public [DockerHub](https://index.docker.io/).

---

### Dependencies

- [ubuntu:bionic (_84.1 MB_\)](https://hub.docker.com/_/ubuntu/)

## Installation

1. Install [Docker](https://www.docker.com/).
2. Download [trusted build](https://store.docker.com/community/images/malice/avast) from public [docker store](https://store.docker.com): `docker pull malice/avast`

## Usage

```
docker run --rm malice/avast EICAR
```

### Or link your own malware folder:

```bash
$ docker run --rm -v /path/to/malware:/malware:ro malice/avast FILE

Usage: avast [OPTIONS] COMMAND [arg...]

Malice Avast AntiVirus Plugin

Version: v0.1.0, BuildTime: 20180903

Author:
  blacktop - <https://github.com/blacktop>

Options:
  --verbose, -V          verbose output
  --elasticsearch value  elasticsearch url for Malice to store results [$MALICE_ELASTICSEARCH_URL]
  --table, -t            output as Markdown table
  --callback, -c         POST results back to Malice webhook [$MALICE_ENDPOINT]
  --proxy, -x            proxy settings for Malice webhook endpoint [$MALICE_PROXY]
  --timeout value        malice plugin timeout (in seconds) (default: 120) [$MALICE_TIMEOUT]
  --help, -h             show help
  --version, -v          print the version

Commands:
  update  Update virus definitions
  web     Create a Avast scan web service
  help    Shows a list of commands or help for one command

Run 'avast COMMAND --help' for more information on a command.
```

## Sample Output

### [JSON](https://github.com/malice-plugins/avast/blob/master/docs/results.json)

```json
{
  "avast": {
    "infected": true,
    "result": "EICAR Test-NOT virus!!!",
    "engine": "2.1.2",
    "database": "17012800",
    "updated": "20170129"
  }
}
```

### [Markdown](https://github.com/malice-plugins/avast/blob/master/docs/SAMPLE.md)

---

#### Avast

| Infected | Result                  | Engine | Updated  |
| -------- | ----------------------- | ------ | -------- |
| true     | EICAR Test-NOT virus!!! | 2.1.2  | 20170129 |

---

> **NOTE:** :warning: License expires in 30 days - https://www.avast.com/linux-server-antivirus

### Use your own license key

```
docker run --rm -v `pwd`/license.avastlic:/etc/avast/license.avastlic malice/avast EICAR
```

## Documentation

- [To write results to ElasticSearch](https://github.com/malice-plugins/avast/blob/master/docs/elasticsearch.md)
- [To create a Avast scan micro-service](https://github.com/malice-plugins/avast/blob/master/docs/web.md)
- [To post results to a webhook](https://github.com/malice-plugins/avast/blob/master/docs/callback.md)
- [To update the AV definitions](https://github.com/malice-plugins/avast/blob/master/docs/update.md)

## Issues

Find a bug? Want more features? Find something missing in the documentation? Let me know! Please don't hesitate to [file an issue](https://github.com/malice-plugins/avast/issues/new).

## TODO

- [ ] add configurable re-try count (cuz this AV is weak sauce **YO!**)
- [ ] add licence expiration detection

## CHANGELOG

See [`CHANGELOG.md`](https://github.com/malice-plugins/avast/blob/master/CHANGELOG.md)

## Contributing

[See all contributors on GitHub](https://github.com/malice-plugins/avast/graphs/contributors).

Please update the [CHANGELOG.md](https://github.com/malice-plugins/avast/blob/master/CHANGELOG.md) and submit a [Pull Request on GitHub](https://help.github.com/articles/using-pull-requests/).

## License

MIT Copyright (c) 2016 **blacktop**
