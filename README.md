# How-To-Get-Computer-System-Information-Using-PowerShell-on-Windows-10
How To Get Computer System Information Using PowerShell on Windows 10

------------

When you want to get system information on windows 10, you can use the built in programs like system info, but you can get a lot of computer information via powershell, like memory, motherboard, installed programs, smart read out, windows updates, event id logs and lots more.

-------------

1. Open PowerShell As an "ADMINISTRATION"

------------

2. Paste the following code

-----------------

Get-WmiObject win32_baseboard; Get-WmiObject Win32_Bios; Get-WmiObject win32_physicalmemory | Select Manufacturer,Banklabel,Configuredclockspeed,Devicelocator,Capacity,Serialnumber; Get-ComputerInfo OSName, OsArchitecture; Get-WmiObject -class win32_quickfixengineering; Get-Disk | Get-StorageReliabilityCounter | Select-Object -Property “*”; Get-CimInstance Win32_OperatingSystem | Select-Object Caption, InstallDate, ServicePackMajorVersion, OSArchitecture, BootDevice, BuildNumber, CSName | FL; Get-LocalUser; Get-ItemProperty HKLM:\Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\* | Select-Object DisplayName, DisplayVersion, Publisher, InstallDate | Format-Table –AutoSize > C:\SystemInformation.txt

------------------

You can also use this code below to get event id

Get-EventLog -LogName system -EntryType Error

--------------

You can also use this code below to get installed programs

Get-WmiObject -Class Win32_Product

-------------------
