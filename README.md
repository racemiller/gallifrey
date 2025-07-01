Still need to start documenting changes.

### Mount Points
Using NFS shares from Enterprise as they seem to work better than SMB. Just switched over so there's still a bit of testing to do. Main reason for switch was each time an *arr container imported/moved/deleted a file, it was doing it twice over the network. For example, a movie would download on Enterprise, then copy over the network to gallifrey, then back over the network to Enterprise in the Data folder. NFS should solve that problem as it allows hardlinking.
If the containers start throwing errors, run "exportfs -au" & "exportfs -a" or possibly just "exportfs -r" as root on Enterprise to restart the NFS shares, then restart the arr-stack on gallifrey.
