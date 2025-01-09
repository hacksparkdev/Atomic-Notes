
Tags: [[Troubleshoot Power and Disk Issues]] [[CompTIA A+]] [[School]] [[Troubleshooting]] 
## Quick Notes

- **Unusual noise (HDD only)** —A healthy hard disk makes a certain low-level noise when accessing the platters. A loud or grinding noise, or any sort of clicking sound , is a sign of a mechanical problem.
- No LED status indicator activity—If disk activity lights are not active, the whole system might not be receiving power, or the individual disk unit could be faulty.
- **Constant LED activity** —Constant activity, often referred to as disk thrashing, can be a sign that there is not enough system RAM so that the disk is being used continually for paging (virtual memory). It could also be a sign of a faulty software process or that the system is infected with malware.
- **Bootable device not found** —If the PC fails to boot from the fixed disk, it is either faulty or there is file corruption.
- Missing drives in OS—If the system boots, but a second fixed disk or removable drive does not appear in tools such as File Explorer or cannot be accessed via the command-line, first check that it has been initialized and formatted with a partition structure and file system. If the disk is not detected by a configuration tool such as Windows Disk Management, suspect that it has a hardware or cable/connector fault.

- **Read/write failure** —This means that when you are trying to open or save a file, an error message such as "Cannot read from the source disk" is displayed. On an HDD, this is typically caused by bad sectors . A sector can be damaged through power failure or a mechanical fault. If you run a test utility, such as chkdsk, and more bad sectors are located each time the test is run, it is a sign that the disk is about to fail. On an SSD, the cause will be one or more bad blocks. SSD circuitry degrades over the course of many write operations. An SSD is manufactured with “spare” blocks and uses wear leveling routines to compensate for this. If the spare blocks are all used up, the drive firmware will no longer be able to compensate for ones that have failed.

- **Blue screen of death (BSOD)**—A failing fixed disk and file corruption may cause a particularly severe read/write failure, resulting in a system stop error (a crash screen).
