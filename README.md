# docker-wsl2-win-free
Run docker on wsl2 (Ubuntu 22)

After Ubuntu 22.04 intallation via Windows Store, follow the steps below:<br>

## Make sure you are using Version 2 of Ubuntu 22.04 (WSL)

Verify that you are running WSL Version 2
Open Command Prompt from the Windows search bar
Run the following command:
```powershell
wsl -l -v
```

You should see a report such as this, which should confirm your WSL Version (NOTE: NAME may differ slightly)
```powershell
  NAME            STATE           VERSION
* Ubuntu-22.04    Stopped         2
```

If your version states version 1, you might need to take an additional step to update Ubuntu.
<br>Enter the following command (NOTE: replace Ubuntu-22.04 with the actual version you installed):
```powershell
wsl --set-version Ubuntu-22.04 2
```

This will take a fair amount of time to complete
<br>Re-Run "wsl -l -v" again to verify your version


## IPTABLES Config

Run the following command:
```console
sudo update-alternatives --config iptables
```

Select "iptables-legacy" option
```{.sh .no-copy}
There are 2 choices for the alternative iptables (providing /usr/sbin/iptables).

  Selection    Path                       Priority   Status
------------------------------------------------------------
  0            /usr/sbin/iptables-nft      20        auto mode
* 1            /usr/sbin/iptables-legacy   10        manual mode
  2            /usr/sbin/iptables-nft      20        manual mode

Press <enter> to keep the current choice[*], or type selection number: 1
```

## Docker installation

Follow "Step 1 — Installing Docker" instructions on link below
<br>https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04


Manage Docker as a non-root user (VS Code on Windows 10 will be able to manage it)
<br>Follow the steps 2 annd 3 on link below
<br>https://docs.docker.com/engine/install/linux-postinstall/
