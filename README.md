# Google cloud print server on Rasberry pi
This ansible playbook configures a freshly installed Raspberry pi as a CUPS print server with google cloud print support.

## Prereq
- Install rasbian on a raspberry pi
- Connect it to your network
- Copy your ssh public key to your servers authorized_keys file. ex. `ssh-copy-id pi@<ip address>`
- Define your pi in the `hosts` file. Here's an example:
```
[cloud-print-server]
<your pi's hostname> ansible_host=<your pi's ip adress> ansible_user=pi ansible_become=yes
```

## Deploy playbook
```
ansible-playbook -i hosts playbook.yml
```
You will get a message to run a command to configure google-cloud-print. Run it and run the playbook again to continue the configuration

## Add printers
Log in to the cups web ui on `https://localhost:631/` to configure a printer.

# Future improvements:
- Rewrite the google-cloud-print to look for a variable `local_only == True` to automatically configure the server as local only and skip the need to have a manually stem in the configuraion.
- Update/set the password for the pi user.
- Configure networking.

## Refrences
Based on: http://www.instructables.com/id/Minimal-Raspberry-Pi-Google-Cloud-Print-Server/
