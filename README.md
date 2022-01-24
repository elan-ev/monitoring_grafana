# Ansible Role for Grafana

![molecule](https://github.com/elan-ev/monitoring_grafana/actions/workflows/molecule.yml/badge.svg)

Install the latest [grafana](https://github.com/grafana/grafana) version with [ansible](https://docs.ansible.com/).

## Role Variables

You can provide your own configuration file as a template.
The role installs the default configuration, which you will likely want to extend or change.
The few options you can set through the role can be found in the [defaults](defaults/main.yml).
To pass your own configuration file, specify the path to the jinja template in the variable `grafana_config_template`.

## Example Playbook

Just add the role to your playbook:

```yaml
- hosts: all
  become: true
  roles:
    - role: elan.monitoring_grafana
      grafana_config_template: 'custom_templates/grafana.ini.j2'
```

## Development

For development and testing you can use [molecule](https://molecule.readthedocs.io/en/latest/).
With podman as driver you can install it like this – preferably in a virtual environment (if you use docker, substitute `podman` with `docker`):

```bash
pip install -r .dev_requirements.txt
```

Then you can *create* the test instances, apply the ansible config (*converge*) and *destroy* the test instances with these commands:

```bash
molecule create
molecule converge
molecule destroy
```

If you want to inspect a running test instance use `molecule login --host <instance_name>`, where you replace `<instance_name>` with the desired value.

## License

[BSD-3-Clause](LICENSE)

## Author Information

[ELAN e.V](https://elan-ev.de/)
