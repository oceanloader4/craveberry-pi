Craveberry Pi
=============

Builds CraveNG on a Raspberry pi.

Building block for a masternode setup.

## base OS

Tested on Debian Jessie 8.0 on a Rpi v3.

## setup

* install Ansible (2.x) on your host machine
* if you've renamed your pi, set correct hostname(s) in 'hosts'
* if you're not using the stock 'pi' user, set ansible_ssh_user' in 'hosts'
* setup passwordless SSH as ansible_ssh_user (i.e. copy up a pubkey to the pi by hand)

You'll need a working internet connection for the install.

## Ansible

You can verify connectivity by running:

    ansible -i hosts all -m ping

and you should see 'pong' from your raspberrypi.

(If you haven't set up an SSH key like i told you to, run

    ansible -i hosts all -m ping -k 

and provide the ssh password - default is 'raspberry'. please change it.)

Run the main play with:

    ansible-playbook -i hosts site.yml

Warning: it'll take a good hour or two. gcc is pretty slow on a pi.

## Quick overview (check the roles for actual details):

* install dev packages
* download, build and install libdb4.8
* create and enable a small (512Mb) swapfile to allow the compilation
* checkout Crave from github and build it

The resulting binaries are in */home/pi/crave-ng/src*

## Next steps

I thought about adding another role to setup crave.conf, etc. 
But then you'd be trusting me to configure your masternode, which
I doubt you'd be happy with.

But you can pick this up on page 8 of [the setup guide|https://crave.cc/pdf/Complete_Masternode_Guide_for_Crave_NextGen.pdf].

I'll add a systemd role soon, to keep craved running on crashes, etc.

## Bugs

Yeah, probably.
Hit me up on the usual social media things, same username as here.

## Donations

Ta very much, like

* CRAVE : VC2MXJfMtaWpsLeeMZ3JywwAB7yFRg6a3m
