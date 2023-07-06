iex ((New-Object System.Net.WebClient).DownloadString('https://boxstarter.org/bootstrapper.ps1')); get-boxstarter -Force

or
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

choco feature enable -n allowGlobalConfirmation


Set-BoxstarterConfig -NugetSources "https://www.myget.org/F/fireeye/api/v2;https://chocolatey.org/api/v2"
# Needed for many applications
# Set up the correct feed
$fireeyeFeed = "https://www.myget.org/F/fireeye/api/v2"
iex "choco sources add -n=fireeye -s $fireeyeFeed --priority 1"
iex "refreshenv"
# iex "choco install -y common.fireeye"
# iex "refreshenv"

choco install impacket.fireeye
choco install impacket-examples-windows.fireeye