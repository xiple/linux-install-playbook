Linux installation playbook
=========

[![CI](https://github.com/xiple/linux-install-playbook/actions/workflows/ci.yml/badge.svg)](https://github.com/xiple/linux-install-playbook/actions/workflows/ci.yml)

This playbook install and configure most of the software I use on my Linux workstation :

- *[RPM fusion](https://rpmfusion.org/)* repositories using [xiple.rpmfusion](https://github.com/xiple/ansible-role-rpmfusion) role,
- *[Visual Studio Code](https://code.visualstudio.com/)* using [xiple.vscode](https://github.com/xiple/ansible-role-vscode) role,
- *[Tailscale](https://tailscale.com/)* using [xiple.tailscale](https://github.com/xiple/ansible-role-tailscale) role,
- *[TLP](https://linrunner.de/tlp/index.html)* using [xiple.tlp](https://github.com/xiple/ansible-role-tlp) role,
- *[Veracrypt](https://veracrypt.jp/)* using [xiple.veracrypt](https://github.com/xiple/ansible-role-veracrypt) role,
- *[Xiple's dotfiles](https://github.com/xiple/dotfiles)* using [geerlingguy.dotfiles](https://github.com/geerlingguy/ansible-role-dotfiles) role,
- *[Docker](https://www.docker.com/)* using [geerlingguy.docker](https://github.com/geerlingguy/ansible-role-docker) role,
- Gnome & Ptyxis shortcuts using ansible [community.general.dconf](https://docs.ansible.com/projects/ansible/latest/collections/community/general/dconf_module.html) module,
- Libvirt & Vagrant virtualization tools,
- Desktop packages and basic customizations. See [vars.yml](https://github.com/xiple/linux-install-playbook/blob/main/vars.yml), [tasks/main.yml](https://github.com/xiple/linux-install-playbook/blob/main/tasks/main.yml) and [tasks/storage.yml](https://github.com/xiple/linux-install-playbook/blob/main/tasks/storage.yml).


Playbook Variables
--------------

```yaml
linux_user: vagrant
```

The desktop user running the playbook.

How to run this playbook ?
----------------

Make sure Ansible is installed

```sh
python3 -m pip install --user ansible
ansible --version
```

In case python3 or pip is not installed

```sh
# tested on Fedora, update below command for your system
sudo dnf install python3
python3 -V

sudo dnf install python3-pip
python3 -m pip -V
```

Install required roles

```sh
ansible-galaxy install -r requirements.yml
```

Run the entire playbook

```sh
ansible-playbook -i inventory.ini \
  --ask-become-pass \
  --extra-vars "linux_user=fedora" \
  main.yml
```

Update `inventory.ini` to run on a specific server (default is localhost).

To run a specific part of the playbook

```sh
ansible-playbook -i inventory.ini \
  --ask-become-pass \
  --extra-vars "linux_user=fedora" \
  --tags gnome \
  --skip-tags tlp \
  main.yml
```

License
-------

MIT

Notes
------------------

Tested on Fedora 43, 44.
