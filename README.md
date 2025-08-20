
## Obivious First Steps:
- Install VMware Workstation Pro
- Create New Virtual Machine
  
### Wizard Settings:
- Hardware Compatibility -> Workstation 17+
- Guest Operating System Installation -> Later
- Guest Operating System -> Windows -> Windows 7 (Or Above)
- Name The Virtual Machine -> "Windows Whatever"
- Location -> Anywhere (This will be where your VMX is located)
- Processor Configuration -> 1 Processor and 4 Cores
- Memory -> 8+gb
- Network Connection -> NAT
- I/O Controller Type -> LSI Logic SAS
- Disk Type -> SCSI
- Select Disk -> New Virtual
- Disk Capacity 128-256gb - Split Into Multiple Files
- Disk File -> Whatever

- Finish!

## VM Settings (Hardware Tab):
![VMSettings](https://i.imgur.com/DzmyvQc.png)

![Advanced](https://i.imgur.com/PfVCOqJ.png)

- Virtualization Engine -> Intel VT-x/EPT or AMD-V/RVI (Disable Your HV if using Windows Sandbox with the command: ``bcdedit /set hypervisorlaunchtype off``)
- CD/DVD(SATA) -> Use ISO Image File -> Your Windows ISO
- Network Adapter -> Avanced Settings -> MAC Address -> Change to FC:34:97:13:33:37 (Anything Other Than VMware Owned Addresses - Don't Click Generate) 

## VM Settings (Options Tab):
![Options](https://i.imgur.com/4vlhgT7.png)

- Advanced -> Firmware Type -> BIOS

## BIOS
Customise your BIOS ROM (Or use pre-supplied one from this project):

![BIOS](https://i.imgur.com/17yqdbV.png)

![Custom](https://i.imgur.com/Zp4osMD.png)

## Customising the .VMX file:
Add the following to your project's VMX file which is located where you've saved the virtual disk data.
```
monitor_control.restrict_backdoor = "TRUE"
monitor_control.disable_directexec = "TRUE"
monitor_control.disable_chksimd = "TRUE"
monitor_control.disable_selfmod = "TRUE"
monitor_control.disable_ntreloc = "TRUE"
monitor_control.disable_reloc = "TRUE"
monitor_control.disable_btmemspace = "TRUE"
monitor_control.disable_btpriv = "TRUE"
monitor_control.disable_btinout = "TRUE"
monitor_control.disable_btseg = "TRUE"
isolation.tools.getVersion.disable = "TRUE"
isolation.tools.setVersion.disable = "TRUE"
isolation.tools.getPtrLocation.disable = "TRUE"
isolation.tools.setPtrLocation.disable = "TRUE"
hypervisor.cpuid.v0 = "FALSE"
board-id.reflectHost = "TRUE"
hw.model.reflectHost = "TRUE"
serialNumber.reflectHost = "TRUE"
smbios.reflectHost = "TRUE"
SMBIOS.noOEMStrings = "TRUE"
scsi0:0.productID = "Cevapi5000"
scsi0:0.vendorID = "Cevapi"
bios440.filename = "C:\<Whatever>\BIOS.440_Cevapi.ROM"
```

## Done!

Enjoy your VMProtect, Themida or whatever application!
