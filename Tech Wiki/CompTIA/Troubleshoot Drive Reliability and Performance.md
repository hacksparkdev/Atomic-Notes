
Tags: [[Troubleshoot Power and Disk Issues]] [[CompTIA A+]] [[School]] [[Troubleshooting]]  #Troubleshooting 

## Quick Notes
### Fixed Disk Diagnostics and Troubleshooting  

1. **SMART (Self-Monitoring, Analysis, and Reporting Technology)**  
   - A built-in diagnostic tool in most fixed disks.  
   - Alerts the OS to potential failures.  

2. **When to Run Diagnostics**  
   - Symptoms: Extended read/write times, performance drops, or suspected drive failure.  
   - Tools:  
     - Use vendor-supplied utilities or system diagnostics programs.  
     - Windows utilities and third-party tools (e.g., SpeedFan) can query SMART data.  

3. **Key Diagnostics**  
   - Detects physical damage or storage mechanism issues.  
   - Reports performance metrics like **IOPS** (Input/Output Operations per Second).  

4. **Interpreting Results**  
   - **Faulty Device**: If metrics deviate significantly from vendor baselines.  
   - **System Performance Issue**: If metrics match baselines but slowness persists, consider:  
     - High application loads or resource constraints.  
     - File fragmentation (on HDDs).  
     - Limited free storage capacity.

5. **Bad Sectors/Blocks**  
   - **Cause**: Specific areas on the disk fail, leading to data loss or corruption.  
   - **Firmware Action**: Marks these areas as unavailable for future use.  

6. **Data Recovery**  
   - Use recovery utilities if files are corrupted or missing and no backup exists.  
   - Recovery software scans the disk to attempt file retrieval.  

---

This summary highlights key points for understanding and troubleshooting fixed disk performance issues and failures.