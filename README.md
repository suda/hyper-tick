# Usage

## Prerequisites

1. [Hyper.sh account](https://console.hyper.sh/register/invite/zMaqodJg30I7aY7JmdBqCQOnWlwprOiG)
2. Any domain that allows A and CNAME records

## Setting up

1. [Configure and install Hyper.sh CLI](https://docs.hyper.sh/GettingStarted/index.html)
2. [Allocate one FIP](https://docs.hyper.sh/Reference/CLI/fip_allocate.html) (if you already allocated it in step 1, you can use this one)
3. Create wildcard CNAME for your domain (i.e. point `*.example.com` to `example.com`)
4. Clone [hyper-tick](https://github.com/suda/hyper-tick)
5. Setup environment with your variables:
```bash
$ export ROOT_DOMAIN=example.com
$ export FIP=201.137.23.3
$ export USERNAME=foo
$ export PASSWORD=bar
```
6. Start the stack from `hyper-tick` directory:
```bash
$ cd hyper-tick
$ hyper compose up -d
```

Now your services should be available under following subdomains (replace `example.com` with domain you used):

* InfluxDB: `influxdb.example.com`
* Chronograf: `chronograf.example.com`
* Kapacitor: `kapacitor.example.com`

Chronograf is the only one that has graphical HTTP interface but you can use [CLI for InfluxDB and Kapacitor](https://www.influxdata.com/downloads/) just remember to pass username and password.

**Warning:** this stack uses `HTTP_BASIC_AUTH` variable of [`dockercloud-haproxy` image](https://github.com/docker/dockercloud-haproxy#global-and-default-settings-of-haproxy) which isn't recommended for production.

You can read more about [rationale of this on my blog](http://suda.pl/cheapest-6-86-hosted-influxdb-chronograf-and-kapacitor-with-hyper-sh/).

# [Contributions welcome](http://contributionswelcome.org/)

All contributions (no matter if small) are always welcome.

Feel free to create [file issues](https://github.com/suda/hyper-tick/issues) or fork this repo and add improvements!
