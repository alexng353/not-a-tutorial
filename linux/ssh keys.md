## ssh key setup on Ubuntu
```bash
ssh-keygen
cat ~/.ssh/id_rsa.pub

# copy the output from cat
# on the server, paste it into 
nano ~/.ssh/authorized_keys
```

