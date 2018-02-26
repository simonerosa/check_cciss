# check_cciss
# HP/HPE Smart Array Hardware status plugin for Nagios

HP Smart Array Hardware status plugin for Nagios with HP Array Configuration Utility CLI and HPE Smart Storage Administrator (hpacucli / hpssacli)

Description:

This plugin checks hardware status for Smart Array Controllers,
using the HP Array Configuration Utility CLI / HPE Smart Storage Administrator.
(Array, controller, cache, battery, etc...)

Examples:

---

    ./check_cciss

    RAID OK
 
 ---
 
    ./check_cciss -v
 
    RAID OK:  Smart Array 6i in Slot 0 array A logicaldrive 1 (67.8 GB, RAID 1+0, OK)
              [Controller Status: OK  Cache Status: OK  Battery Status: OK]

    RAID CRITICAL - HP Smart Array Failed:  Smart Array 6i in Slot 0 (Embedded) \
             array A logicaldrive 1 (33.9 GB, RAID 1, Interim Recovery Mode) \
             physicaldrive 1:0 (port 1:id 0 , Parallel SCSI, --- GB, Failed)

    RAID WARNING - HP Smart Array Rebuilding:  Smart Array 6i in Slot 0 (Embedded) \
             array A logicaldrive 1 (33.9 GB, RAID 1, Recovering, 26% complete) \
             physicaldrive 1:0 (port 1:id 0 , Parallel SCSI, 36.4 GB, Rebuilding)

---
    ./check_cciss -v -p
  
    RAID OK:  Smart Array 6i in Slot 0 (Embedded) array A logicaldrive 1 (33.9 GB, RAID 1, OK)
              physicaldrive 2:0 (port 2:id 0 , Parallel SCSI, 36.4 GB, OK)
              physicaldrive 2:1 (port 2:id 1 , Parallel SCSI, 36.4 GB, OK)
              physicaldrive 1:5 (port 1:id 5 , Parallel SCSI, 72.8 GB, OK, spare)
              [Controller Status: OK Cache Status: OK Battery/Capacitor Status: OK]

    RAID CRITICAL - HP Smart Array Failed:  Smart Array 6i in Slot 0 (Embedded) \
             array A logicaldrive 1 (33.9 GB, RAID 1, Interim Recovery Mode) \
             physicaldrive 1:0 (port 1:id 0 , Parallel SCSI, --- GB, Failed) \
             physicaldrive 1:1 (port 1:id 1 , Parallel SCSI, 36.4 GB, OK)

    RAID WARNING - HP Smart Array Rebuilding:  Smart Array 6i in Slot 0 (Embedded) \
             array A logicaldrive 1 (33.9 GB, RAID 1, Recovering, 26% complete) \
             physicaldrive 1:0 (port 1:id 0 , Parallel SCSI, 36.4 GB, Rebuilding) \
             physicaldrive 1:1 (port 1:id 1 , Parallel SCSI, 36.4 GB, OK)

---

    ./check_cciss -v -b
 
    RAID OK:  Smart Array 6i in Slot 0 (Embedded) array A logicaldrive 1 (33.9 GB, RAID 1, OK) [Controller Status: OK]

    RAID CRITICAL - HP Smart Array Failed:  Smart Array 6i in Slot 0 (Embedded) \
                    Controller Status: OK Cache Status: Temporarily Disabled \
                    Battery/Capacitor Status: Failed (Replace Batteries/Capacitors)
