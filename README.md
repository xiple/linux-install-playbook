Linux installation playbook
=========

This playbook install and configure most of the software I use on my Linux workstation.

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
  main.yml
```

License
-------

MIT

Notes
------------------

Tested on Fedora 42
