# Examination 1 - Understanding SSH and public key authentication

Connect to one of the virtual lab machines through SSH, i.e.

    $ ssh -i deploy_key -l deploy webserver

Study the `.ssh` folder in the home directory of the `deploy` user:

    $ ls -ld ~/.ssh

Look at the contents of the `~/.ssh` directory:

    $ ls -la ~/.ssh/

## QUESTION A

### What are the permissions of the `~/.ssh` directory?
#### drwx------, ägaren har fulla rättigheter, resterande ingenting alls
 

### Why are the permissions set in such a way?
#### Av säkerhetsskäl i och med att det är känsliga uppgifter inuti filen och i fel händer kan obehöriga komma åt datorn via ssh


## QUESTION B

### What does the file `~/.ssh/authorized_keys` contain?
#### Publika nycklar. 

## QUESTION C

### When logged into one of the VMs, how can you connect to the other VM without a password?
#### Genom att använda sig utav ssh. Man genererar en privat och en publik nyckel för att komma åt den andra VMn utan att behöva använda ett lösenord.

### Hints:

* man ssh-keygen(1)
* ssh-copy-id(1) or use a text editor

## BONUS QUESTION

### Can you run a command on a remote host via SSH? How?
#### Ja, det kan man göra. I och med att med ssh loggar man in i den andra datorn så allt man gör i terminalen efter du har ssh in dig görs på den andra datorn, fram tills att du "loggar ut".