<div align="center">
  <img src="screenshots/display.png" alt="Windows CodeDefender Screenshot" />
</div>

# Windows CodeDefender

This repository contains a VirtualBox snapshot of Windows 10 version 1507 running with obfuscated `ntoskrnl.exe` and `bootmgfw.efi` files. If you would like to see additional files obfuscated or additional functions obfuscated, feel free to join our community and ask! [Join our Discord](https://discord.gg/sgedeapTMm)

## Overview

This project demonstrates CodeDefenders ability to obfuscate kernel and bootloader files. The modified system includes obfuscated critical system functions and bypassed security mechanisms.

The snapshot is compressed and spread over several ZIP files. All of these can be found in the `snapshot` folder. The password for the ZIP file is `password`. Simply open the `Windows-CodeDefender.zip` and it should automatically detect the rest of the zip files. You will need to install `VirtualBox` with `Version 7.2.2` or newer. 

### ntoskrnl.exe

The following functions/RVAs have been obfuscated within the Windows kernel:

```
0x482204 - NtOpenFile
0x482310 - IopCreateFile
0x272960 - ExAllocatePoolWithTag
0x155E00 - KiDivideErrorFault
0x482C40 - NtQuerySystemInformation
0x482D60 - ExpQuerySystemInformation
0x155F00 - KiDebugTrapOrFault
0x2057F4 - MmCopyMemory
0x43B940 - MmCopyVirtualMemory
0x5B840  - MiStealPage
```

Additionally, driver signing enforcement and other PatchGuard-related functions have been patched out. The modifications are based on information from the [UPGDSED repository](https://github.com/hfiref0x/UPGDSED/blob/master/src/patterns.h). 

> Not every function in the kernel is obfuscated for performance reasons, if you want to see certain kernel functions obfuscated feel free to ask us!

### bootmgfw.efi

The `ImgpValidateImageHash` function has been patched following the methodology from [EfiGuard](https://github.com/Mattiwatti/EfiGuard). All available functions within bootmgfw have been obfuscated using a light to medium level obfuscation preset.

<div align="center">
  <img src="screenshots/boot-selection.png" alt="Windows CodeDefender Screenshot" />
</div>