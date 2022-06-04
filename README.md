# docker-wsl2-win-free
Run docker on wsl2 (Ubuntu 22)

After Ubuntu 22.04 intallation via Windows Store, follow the steps below:

# Ubuntu 22.04 WSL Version

Verify that you are running WSL Version 2
Open Command Prompt from the Windows search bar
Run the following command:

wsl -l -v

You should see a report such as this, which should confirm your WSL Version (NOTE: NAME may differ slightly)

wsl --set-version Ubuntu-22.04 2


If your version states version 1, you might need to take an additional step to update Ubuntu:
Enter the following command (NOTE: replace Ubuntu-22.04 with the actual version you installed):
wsl --set-version Ubuntu-22.04 2

This will take a fair amount of time to complete
Re-Run the "wsl -l -v" to verify your version


# IPTABLES Config

Run the following command:
sudo update-alternatives --config iptables

Select "iptables-legacy" option

/usr/sbin/iptables-legacy

# Docker installation

Follow "Step 1 — Installing Docker" instructions on link below 
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04
