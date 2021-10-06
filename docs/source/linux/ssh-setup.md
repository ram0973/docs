### Setup ssh in Ubuntu 

```bash
# create key if needed or skip and copy your key to ~/.ssh/id_rsa, if existed
$ ssh-keygen -t rsa -b 4096 -C "your_mail@your_domain"
$ chmod 400 ~/.ssh/config
$ chmod 400 ~/.ssh/id_rsa

# Ssh-agent: add next two lines to ~/.bashrc
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa

$ source ~/.bashrc

# Go to github and paste contents of ~/.id_rsa.pub there https://github.com/settings/ssh/new
# Test key on github
$ ssh -T git@github.com
# change passphrase if desired: $ ssh-keygen -p
```

Write in ~/.ssh/config:
```
Host dev
  Hostname localhost
  Port 2222
  User vagrant
  IdentityFile ~/.ssh/id_rsa
  StrictHostKeyChecking no
Host staging
  Hostname localhost
  Port 2223
  User vagrant
  IdentityFile ~/.ssh/id_rsa
  StrictHostKeyChecking no
Host prod
  Hostname domain_name
  Port XXXX # ssh port on production server
  User user_name
  IdentityFile ~/.ssh/id_rsa
```

```
