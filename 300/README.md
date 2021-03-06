# 300 - Deploy OpenFaaS

See https://github.com/vanHeemstraSystems/openfaas-workshop-headstart

In sum, deploy OpenFaaS with Kubernetes or with faasd, pick one and follow the instructions: [OpenFaaS Deployment](https://docs.openfaas.com/deployment/)


Here we decide to deploy OpenFaaS with faasd (as it is only intended for the development of a function).

Hence we follow this instruction: 

---
## faasd - Serverless for everyone else

faasd is OpenFaaS, reimagined without the complexity and cost of Kubernetes. It runs well on a single host with very modest requirements, and can be deployed in a few moments. Under the hood it uses [containerd](https://containerd.io/) and [Container Networking Interface (CNI)](https://github.com/containernetworking/cni) along with the same core OpenFaaS components from the main project.

When should you use faasd over OpenFaaS on Kubernetes?

- You have a cost sensitive project - run faasd on a 5-10 USD VPS or on your Raspberry Pi
- When you just need a few functions or microservices, without the cost of a cluster
- When you don't have the bandwidth to learn or manage Kubernetes
- To deploy embedded apps in IoT and edge use-cases
- To shrink-wrap applications for use with a customer or client

[Deploy faasd](https://github.com/openfaas/faasd/):

***WARNING***: It's recommended that you do not install Docker on the same host as faasd, since 1) they may both use different versions of containerd and 2) docker's networking rules can disrupt faasd's networking. When using faasd - make your faasd server a faasd server, and build container image on your laptop or in a CI pipeline.

In short, run these commands to install faasd:

```
$ git clone https://github.com/openfaas/faasd --depth=1
```

```
$ cd faasd
$ ./hack/install.sh
```

This will result in:

```
2021/05/11 15:13:03 Writing to: "/var/lib/faasd/secrets/basic-auth-password"
2021/05/11 15:13:03 Writing to: "/var/lib/faasd/secrets/basic-auth-user"
Check status with:
  sudo journalctl -u faasd --lines 100 -f

Login with:
  sudo cat /var/lib/faasd/secrets/basic-auth-password | faas-cli login -s
Skipping caddy installation as FAASD_DOMAIN.
```
---

Check the status as recommened above:

```
$ sudo journalctl -u faasd --lines 100 -f
```

Use the instructions given to you to log in with ```$ faas-cli login```

You can try out one of the sample functions from the Function Store.

For instance The function named hubstats will tell you how many Docker Hub images a user has. I typed in my user account and found out I have almost 200 already!

![hubstats](https://user-images.githubusercontent.com/12828104/117837972-30d5bc00-b27a-11eb-90d4-46cb16aa71f9.png)

To deploy it yourself run:

```
$ faas-cli store list
$ faas-cli store deploy hubstats
```
 ***Note***: this function is not available for Raspberry Pi at this time.
