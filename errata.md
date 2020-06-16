# OpTC Data Errata

Known OpTC dataset issues:

* **Duplicate Process Objects**: Multiple process sources aren’t de-conflicted properly. Only one is used further as the correlated process object.

* **Executable Hashes Not Included In Module Loads**: Hashes in process executions are missing in module loads (DLLs).

* **Zero Acuity Data Level**: eCAR data property acuity_level is 0 for FLOW OPEN events, expected 1-5 for adaptive response categories.

* **File Paths Use Disk Devices**: Path representation changes between using standard drive naming (i.e. C:) and internal device storage naming (/device/HardDisk0/) depending on property type.





Distribution A: Approved for public release: distribution unlimited
