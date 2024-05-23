ElasticSearch Fluentd and Kibana

Installation steps:
- Add helm Repo:
    $ helm repo add efk https://sachinniveus.github.io/observability/
- Create a namespace
    $ kubectl create ns logging
- Install the stack
    $ helm install efk efk/efk -n logging
