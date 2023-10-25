# Heimdall

Install Heimdall on a Kubernetes cluster.

[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-heimdall-blue.svg)](https://galaxy.ansible.com/ui/standalone/roles/rmasters270//heimdall)

## Requirements

### Localhost

The role is intended to run from the Ansible controller.  If the playbook is executed on a different host it will fail because the templates must be copied to the target host.

### Kube Config

The host and user running the playbook must have kube config configured.

### Helm

The host must have the Helm package manager installed.

## Role Variables

| Variable              | Required | Default                           | Comments                                   |
| --------------------- | -------- | --------------------------------- | ------------------------------------------ |
| heimdall_namespace    | yes      | heimdall                          | Kubernetes namespace                       |
| heimdall_repo_name    | yes      | k8s-at-home                       | Helm repository name                       |
| heimdall_repo_url     | yes      | <https://k8s-at-home.com/charts/> | Helm repository URL                        |
| heimdall_repo_version | yes      | 8.3.2                             | Helm chart version                         |
| heimdall_hostname     | yes      | heimdall.{{ ansible_domain }}     | Heimdall hostname for Traefik ingressroute |

## Dependencies

Use `rmasters270.helm` role or install `kubernetes cli` and `helm` manually on the host.

Setup `kube config` for the user account and host.

## Example Playbook

```yaml
- hosts: localhost

  roles:
    - rmasters270.helm
    - rmasters270.traefik
    - rmasters270.heimdall
```

## License

MIT

## Author Information

Ryan Masters
