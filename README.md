# Ifgy - Ansible-HestiaCP

This is a [HestiaCP Control Panel](https://hestiacp.com/) installer based on [ansible](https://www.ansible.com/) role.

Tests are built in [Molecule](https://github.com/ansible/molecule) with [Vagrant](https://www.vagrantup.com/).

This code is a fork of an excelent work developed by https://github.com/softasap/sa-box-vestacp

## Usage

Example of usage:

Simple

```yaml
- { role: "ansible_hestiacp" }
```

Advanced

```yaml
- {
    role: "ansible_hestiacp",
    hestia_hostname: "{{ inventory_hostname }}",
    hestia_email: "user@domain.tld",
    hestia_password: "password",
    hestia_port: 8083,
    hestia_lang: en,
    option_apache: yes,
    option_phpfpm: no,
    option_multiphp: yes,
    option_vsftpd: yes,
    option_proftpd: no,
    option_named: yes,
    option_mysql: no,
    option_mysql8: yes,
    option_postgresql: no,
    option_exim: yes,
    option_dovecot: yes,
    option_sieve: no,
    option_clamav: yes,
    option_spamassassin: yes,
    option_iptables: yes,
    option_fail2ban: yes,
    option_quota: no,
    option_api: yes,
  }
```

## Usage with ansible galaxy workflow

If you installed the `ansible_hestiacp` role using the command:

```bash
    $ ansible-galaxy install ifgy.ansible_hestiacp
```

the role will be available in the folder `library/ifgy.ansible_hestiacp`
Please adjust the path accordingly.

```yaml
- { role: "ifgy.ansible_hestiacp" }
```

# Development

## Setup Environment

Basic setup of a development, first [install molecule](https://ansible.readthedocs.io/projects/molecule/installation/) and [install vagrant](https://developer.hashicorp.com/vagrant/docs/installation).

### Step 1: Initialize a new scenario with Molecule

```bash
    molecule init scenario -d vagrant
```

### Step 2: Configure your role’s dependencies

Edit files:

```
    $ vim /molecule/default/molecule.yml
```

### Step 3: Test your role

```bash
    $ molecule create ## create the VM and prepare it
    $ molecule login ## log in to the VM and check the installation
    $ molecule converge  ## deploy your role - converge.yml
    $ molecule verify ## validate to production - verify.yml
    $ molecule destroy ## delete the VMs that we just created
    $ molecule test ## which will run all of the steps
```

# References

- https://github.com/ansible/molecule
- https://github.com/ansible-community/molecule-vagrant
- https://github.com/netresearch/molecule_http_docker_demo
- https://ansible.readthedocs.io/projects/molecule/installation/#source
- https://www.netresearch.de/en/blog/ansible-molecule-vagrant-testing-optimize/

# Copyright and license

Code is dual licensed under the [BSD 3 clause](https://opensource.org/licenses/BSD-3-Clause) and the [MIT License](http://opensource.org/licenses/MIT). Choose the one that suits you best.
