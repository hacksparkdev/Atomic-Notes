Tags: [[Troubleshoot Power and Disk Issues]] [[CompTIA A+]] [[School]] [[Troubleshooting]]  [[POST]] #Troubleshooting

## Quick Notes

**Power-on self-test (POST)**
- The POST  is a diagnostic program implemented in the system firmware that checks the hardware to ensure the components required to boot the PC are present and functioning correctly.
![[Screenshot 2024-11-18 121556.png]]

Here’s a bitesize breakdown you can study:

---

### Boot Process and Troubleshooting  
1. **POST and Boot Sequence**  
   - **POST Tests**: Power-On Self-Test checks hardware.  
   - **Boot Sequence**: Firmware searches devices in a set order (e.g., fixed disk → USB → network).  
   - **Errors**: If no boot device is found, the system halts and shows an error.  

2. **Common Troubleshooting Steps**  
   - **Incorrect Device Boot**:  
     - Remove interfering media from removable drives.  
     - Check boot order in BIOS/UEFI.  
   - **Fixed Disk Not Detected**:  
     - Verify power (LED indicator or spinning noise).  
     - Ensure data cables are connected and undamaged.  
     - Check motherboard settings (jumpers or BIOS settings).

---

### Boot Sector Issues  
1. **What Causes Boot Sector Problems?**  
   - Corruption from disk faults, power failure, OS installation errors, or malware.  

2. **Boot Information Formats**  
   - **MBR (Master Boot Record)**:  
     - First sector of the first partition contains partition and boot info.  
     - Active partition points to OS boot loader (e.g., BCD, GRUB, or LILO).  
   - **GPT (GUID Partition Table)**:  
     - Boot info spans multiple sectors but works similarly to MBR.

3. **Symptoms of Boot Sector Issues**  
   - Errors like "Boot device not found" or "Invalid drive specification."  

4. **Fixes**  
   - Use antivirus boot disk to detect malware and repair.  
   - Use OS setup disk repair options if no recovery disk is available.

---

### OS Errors and Crashes  
1. **When OS Loads**  
   - Boot sector code loads OS files into memory.  
   - Errors after this point are likely software or driver issues.  

2. **Critical Errors (BSOD)**  
   - **Causes**: Memory faults, driver issues, or corrupted OS files.  
   - **Steps**:  
     - Scan QR code on BSOD for help.  
     - Check **System Logs** (look for Bug Check events).  
     - Analyze memory dump if available.  

---

This summary simplifies the technical content while preserving key details for study.