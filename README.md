# GetDisk
- The purpose of this project is to provide the command to get GUID of a drive and Host Bus Adapter (HBA) information for EXPRESSCLUSTER configuration file of **Windows**.

## Sample Configuration
- R: drive is for disk method network partition resolution resource (disknp).
- S: drive is for disk resource.
- R: and S: are on the same shared storage under the same HBA.

## How to Use
1. Install EXPRESSCLUSTER and restart OS.
1. Save the clpgetdisk.exe and runtime dll on some directory.
1. Run the following command.
   -  Get the GUID of volume for disknp.
      ```powershell
      PS> $hostname = hostname
      PS> .\clpgetdisk.exe guid R:\ > ${hostname}_disknp.csv
      PS> Get-Content ${hostname}_disknp.csv
      volumeguid,drive
      019056a3-a7ad-4de3-9ed8-d5e752e501ea,R:\
      ```
   - Get the GUID of 
      ```powershell
      PS> $hostname = hostname
      PS> .\clpgetdisk.exe guid R:\ > ${hostname}_sd.csv
      PS> Get-Content ${hostname}_sd.csv
      volumeguid,drive
      205bce9a-e322-442d-af11-776f8b6af913,S:\
      ```
   - Get the HBA
     ```powershell
     PS> .\clpgetdisk.exe hba S:\ > ws2016-197_hba.csv
     PS> Get-Content ws2016-197_hba.csv
     portnumber,deviceid,instanceid
     4,ROOT\ISCSIPRT,0000
     ```
1. Copy the above files and run the clpcreate command as [sample script](https://github.com/EXPRESSCLUSTER/CreateCluster/tree/master/script).