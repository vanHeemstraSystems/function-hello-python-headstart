# 200 - Install the OpenFaaS CLI

See https://github.com/vanHeemstraSystems/openfaas-cli-headstart

The CLI is a convenient way to interact with your functions. You can use it to build and/or deploy functions to your cluster.

In short, on Linux type in:

```
$ curl -sSL https://cli.openfaas.com | sudo sh
```

Check your installation as follows:

```
$ faas-cli version
  ___                   _____           ____
 / _ \ _ __   ___ _ __ |  ___|_ _  __ _/ ___|
| | | | '_ \ / _ \ '_ \| |_ / _` |/ _` \___ \
| |_| | |_) |  __/ | | |  _| (_| | (_| |___) |
 \___/| .__/ \___|_| |_|_|  \__,_|\__,_|____/
      |_|

CLI:
 commit:  2cec97955a254358de5443987bedf8ceee272cf8
 version: 0.13.9
```

***Note***: If you're using Windows, then you're not out of luck, you can actually find the Windows executable on the [FaaS releases page](https://github.com/openfaas/faas-cli/releases/tag/0.4.5-b).
