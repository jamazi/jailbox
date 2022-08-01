# jailbox
Redirect Linux tcp connections through multiple load-balanced tor connections with ability to use direct internet for specific programs.

## Installation:
### Manual:
- Install Tor:

    debian:

        sudo apt install tor

- Clone this repository:

        git clone https://github.com/jamazi/jailbox.git

- Run setup script:

        sudo ./setup

### Archlinux users:
        yay -S jailbox-git


<br />

## Usage:
- Edit configurations *(optional)*:

        sudo nano /etc/jailbox/config

- Start jailbox:

        sudo jailbox-start

  or:

        sudo systemctl start jailbox

- Run program with direct internet connection, examples:

  shell on current user:

        sudo -E unjailbox

  firefox with specific profile:

        sudo -E unjailbox -c "firefox --new-instance -P clearnet"

  curl on specific user:

        sudo unjailbox -u root curl -v ifconfig.me

- Stop jailbox:

        sudo jailbox-stop

  or:

        sudo systemctl stop jailbox

<br />

Some usefull config:
====================

`default_nameservers`: this is the default dns servers used for unjailed programs or when jailbox is stopped.

`tor_count`: how many tor connections should be used to load balance your connections through them.

`allowed_ports`: accept incomming tcp connections to this port (like if you want to accept ssh connections).

`allowed_input_lan`: accept any inbound connections from this address list (eg: `allowed_input_lan="192.168.0.0/16"`).

`restrictive`: if ***not*** `0` jailbox will drop packets before they reach other filter rules, otherwise jailbox will deliver packets to other filter rules.

`allow_udp`: if `1` jailbox will allow outgoing udp connections ***without*** being torifyed.

`allow_ping`: if `1` jailbox will allow outgoing ping requests ***without*** being torifyed.

`PreStart/PostStart/PreStop/PostStop`: Command to run automatically before or after jailbox start/stop, jailbox-post-start and jailbox-pre-stop scripts can be used here to prevent leak while restarting jailbox.
