# Ansible Role K8s Tools

[![CI](https://github.com/oscaromeu/ansible-role-k8s-tools/actions/workflows/ci.yml/badge.svg)](https://github.com/oscaromeu/ansible-role-k8s-tools/actions/workflows/ci.yml)

This role installs all or some of the following k8s utilities:
- [Helm](https://helm.sh)
- [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
- [Flux V2](https://fluxcd.io/docs/cmd/)
- [Kustomize](https://kustomize.io/) <= TODO
- [K3d](https://k3d.io/v5.3.0/) <= TODO

## Requirements

N/A

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```
uninstall_tools: true
```

If set to true it will only remove the installed cli's. Use with `--skip-tags` to only remove the cli's not listed in it.

```yml
k8s_platform: linux
k8s_arch: arm64
```

By default the platform is `linux` and the `architecture` is `arm64`. These variables are checked and configured at runtime by the role so its not necessary to adjust them.

```yml
helm_version: 'v3.2.1'
kubectl_version: "1.21.2"
flux_version: "0.27.3"
```

Using these variables the binaries can be upgraded or downgraded. 


```yml
helm_bin_path: /usr/local/bin/helm
kubectl_bin_path: /usr/local/bin/kubectl
flux_bin_path: /usr/local/bin/flux
```

The location where the helm/kubectl binary will be installed.

## Dependencies

None.

## Examples

### Example Playbook

```yaml
    - hosts: all
      roles:
        - role: oscaromeu.k8s_tools
```

### Execute example playbook locally

```
ansible-playbook --connection=local --inventory 127.0.0.1, playbook.yml --ask-become-pass
```

### Execute test with molecule and skip kubectl install

```
molecule converge -s default -- --skip-tags=kubectl
```


## License

MIT / BSD

## Author Information

This role was created by Oscar Romeu based on [ansible-role-k8s_cli](https://github.com/ricsanfre/ansible-role-k8s_cli)
 

