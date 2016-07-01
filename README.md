Consul Server
------------------

[Consul](https://www.consul.io) server based on docker containers.

### prerequisite
* [docker](https://www.docker.com/products/docker) is needed, 据说楼主安装了最新款的docker.app
* docker-compose，如果是在mac上就不需要再次安装了，安装了docker.app就有docker-compose了，至于linux么，楼主不知道啊

理论上，只要上面两个就可以了，如果还需要别的，请提个issue。

### how to run?
* `cd infrastructure`
* `docker-compose up`
* then open [localhost:10085/ui](localhost:10085/ui) in your browser

### infrastructure
* there are two consul servers: consul-server-1, consul-server-2. And one consul agent consul-web-ui, it is used to host the consul ui.

### directory explaination
* infrastructure，it contians configuration files for docker docker-compose
* folder with 'config' suffix is configuration for each consul agent in each container
* one.yml inside infrastructure folder is a single consul server with ui enabled, just used to test the way to configure ui page

### anything else
* if you get into the ui container, then curl localhost:8500, you will get 301, don't panic, that's correct. If you use a browser to access localhost:8500, you will get the ui page. Another way is to use `curl -vL localhost:8500`, `-v` shows more info and `-L` follows the redirects. Next time, when you use curl and there is 301 returned, please use `curl -vL`.
* before consul 0.6.1, you need to download the consul webui zip. As we are using consul 0.6.4, so we can use the internal ui.
* you need to assign `-client` or `client_addr` for the ui agent, otherwise you cannot access it through docker port. For the reason, check [https://www.consul.io/docs/agent/options.html#_client](https://www.consul.io/docs/agent/options.html#_client)
