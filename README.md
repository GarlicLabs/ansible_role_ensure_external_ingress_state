# ansible_role_ensure_external_ingress_state

[![Validate infrastructure as code](https://github.com/garliclabs/ansible_role_ensure_external_ingress_state/actions/workflows/validation.yml/badge.svg)](https://github.com/garliclabs/ansible_role_ensure_external_ingress_state/actions/workflows/validation.yml)

Deploys nginx ingress to your kubernetes cluster as NodePorts, so your cluster will be reachable from the outside.  
Use this if you want to have external reachable k8s cluster without using loadbalancer services.   

## Requirements

Helm, Kubernetes

## Role Variables

```yaml
external_ingress_state
external_ingress_proxy_body_size

external_ingress_replica_count
external_ingress_min_available

external_ingress_create_namespace

external_ingress_kubeconfig
external_ingress_chart_version
external_ingress_namespace

external_ingress_http_port
external_ingress_https_port
external_ingress_tcp_port
```

**external_ingress_state:** State of the ingress deployment can be either present or absent
**external_ingress_proxy_body_size:** The maxiumum size of request bodies the webserver will accept
**external_ingress_replica_count:** Count of replication
**external_ingress_min_available:** Minimum available ingress deployments
**external_ingress_create_namespace:** Is the deployment allowed to create a new namespace
**external_ingress_kubeconfig:** Specify the path to your kubeconfig, so the role can deploy to your kubernetes cluster
**external_ingress_chart_version:** Version of the chart that will be deployed
**external_ingress_namespace:** Namespace in that the ingress will be deployed
**external_ingress_http_port:** External reachable http port
**external_ingress_https_port:** External reachable https port
**external_ingress_tcp_port:** External reachable tcp port

## Development

### Testing

* Create venv: `python3 -m venv ./venv`
* Install pip requirements: `venv/bin/pip install -r pip_requirements.txt`
* Execute tests `venv/bin/molecule test`

### Linting & static security analyser

Both the linter and the static security analyser are running on each push on the github actions pipeline.  

* As linter [ansible-lint](https://ansible.readthedocs.io/projects/lint/) is used. For installation documentation see [ansible lint installing](https://ansible.readthedocs.io/projects/lint/)
  * Just run `ansible-lint`

* To check if there are any passwords, tokens... hardcoded, [kics](https://kics.io/index.html) is used to ensure a secure IaC repository.  
  * Run it locally `docker run -t -v $PWD:/path checkmarx/kics:latest scan -p /path -o "/path/"`

## Dependencies

None.

## License

GNU General Public License version 3
