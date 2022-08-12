[SOLVED - FreeNAS-11.2-U3 - Ubuntu 18.04 server in VM has no internet access. | TrueNAS Community](https://www.truenas.com/community/threads/freenas-11-2-u3-ubuntu-18-04-server-in-vm-has-no-internet-access.75684/)

```bash
ip a # note down if the number on enp0s<n>
cd /etc/netplan
ls # note down whatever the fuck this spits out
vim <int>-installer-config.yaml
# change enp0s5 to whatever <n> was
# exit and then
sudo netplan apply
ping 1.1.1.1 # and double check if it works, if it doesn't, reset the system lmAo
```