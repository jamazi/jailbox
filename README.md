# jailbox
Redirect Linux tcp connections through multiple load-balanced tor connections with ability to use direct internet for specific programs.

Instructions:
=============

1. Install Tor:

    debian


        sudo apt install tor

    arch

        sudo pacman -S tor

2. Clone this repository: 

        git clone https://github.com/jamazi/jailbox.git

3. Run setup: 

        sudo ./setup

4. *(optional)* Edit configurations:

        sudo vim /etc/jailbox/config

5. Start jailbox:

        sudo jailbox-start

6. Run program with direct internet connection:

        sudo -E unjailbox -u user -c firefox --new-instance -P clearnet

7. Stop jailbox:

        sudo jailbox-stop

    
### Or you can use systemd to start and stop jailbox service ###


<br />

Some usefull config:
====================

`default_nameservers`: this is the default dns servers used for unjailed programs or when jailbox is stopped.

`tor_count`: how many tor connections should be used to load balance your connections through them.

`allowed_ports`: accept incomming tcp connections to this port (like if you want to accept ssh connections).

`restrictive`: if `1` jailbox will drop packet before they get to other filter rules, otherwise jailbox will deliver packets to other filter rules.

`PreStart/PostStart/PreStop/PostStop`: Command to run automatically before or after jailbox start/stop.