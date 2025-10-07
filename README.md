# Linux automated installation

## Requirements

Install required roles

```sh
ansible-galaxy install -r requirements.yml
```

### Fedora 42

`python3-libdnf5` package is necessary for ansible dnf module to work.
