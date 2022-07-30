# Copy file or config to all hosts

in this example ansible copy a file to all hosts

## Target machines:

```YAML
hosts: all
```

## How to run:

```BASH
ansible-playbook copy.yml
```

### note:

if you don't want use sudo, you can comment out the line

```YAML
sudo: true
```

## How to run as sudo user:

```BASH
ansible-playbook copy.yml --ask-become-pass
```

`--ask-become-pass` is a special option that asks for sudo password.

# Restart service after copy config to hosts

if you want to restart service after copy config, you see the second task, otherwise you can comment out the second task.

```YAML
    - name: restart tor service
      systemd:
        name: tor
        state: restarted
```

dont forget config ansibe:

`/etc/ansible/hosts`

### log:

if you dont't want to see the log, you can comment out the lines

```YAML
    register: copy
```

```YAML
    - debug: var=copy
```
