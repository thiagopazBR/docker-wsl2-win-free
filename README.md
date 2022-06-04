# docker-wsl2-win-free
Run docker on wsl2 (Ubuntu)

This mini tutorial allows you to install docker without docker desktop on windows.
<br>The iptables section is the trick to enable "internet" connection inside docker containers.

- If Docker Desktop is installed you have to uninstall it. -

## Enable WSL

<br>In Windows, the Linux Subsystem has to be enabled. This can be done running the follow PowerShell command (administrative privileges required):
```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

## Install Ubuntu on WSL2
After you set up the prerequisite above, you have to open a PowerShell with administrative privileges and install Ubuntu in WSL2 with the following command:
```powershell
wsl --set-default-version 2
wsl --install -d Ubuntu
```
After the installation is finished you should check if Ubuntu was installed in the correct version:
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
This will take a fair amount of time to complete. Re-Run "wsl -l -v" to verify your version.


## IPTABLES Config

Run the following command:
```console
sudo update-alternatives --config iptables
```

Select "iptables-legacy" option
```{.text .no-copy}
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
