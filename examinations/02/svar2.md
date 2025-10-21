## QUESTION A

### What happens if you run `ansible-inventory --list` in the directory you created above?

```bash
{
    "_meta": {
        "hostvars": {
            "192.168.121.16": {
                "ansible_ssh_private_key_file": "/home/administrator/devops24/lab/deploy_key",
                "ansible_user": "deploy"
            },
            "192.168.121.207": {
                "ansible_ssh_private_key_file": "/home/administrator/devops24/lab/deploy_key",
                "ansible_user": "deploy"
            }
        }
    },
    "all": {
        "children": [
            "ungrouped",
            "db",
            "web"
        ]
    },
    "db": {
        "hosts": [
            "192.168.121.207"
        ]
    },
    "web": {
        "hosts": [
            "192.168.121.16"
        ]
    }
}
```
Detta visar min inventory i JSON-format. Den visar alltså mina två VMs som jag lade in i 'hosts' samt dess information. 

## QUESTION B

### What happens if you run `ansible-inventory --graph` in the directory you created above?

```bash
@all:
  |--@ungrouped:
  |--@db:
  |  |--192.168.121.207
  |--@web:
  |  |--192.168.121.16
```
Detta är också en vy av min inventory men kortare info. En "tree-view" där jag ser mina VMs samt deras IP-adress

## QUESTION C

### In the `hosts` file, add a new host with the same hostname as the machine you're running ansible on:

    [controller]
    <hostname_of_your_machine> ansible_connection=local

### Now run:

    $ ansible -m ping all

### Study the output of this command.

### What does the `ansible_connection=local` part mean?

```bash
10.6.69.51 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
192.168.121.207 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
192.168.121.16 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
``` 
Det innebär att den inte ska söka utanför utan denna IP-adress är lokalt i nätet. 



