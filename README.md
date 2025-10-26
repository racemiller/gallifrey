Still need to start documenting changes.

## Mount Points
~~Using NFS shares from Enterprise as they seem to work better than SMB. Just switched over so there's still a bit of testing to do. Main reason for switch was each time an *arr container imported/moved/deleted a file, it was doing it twice over the network. For example, a movie would download on Enterprise, then copy over the network to gallifrey, then back over the network to Enterprise in the Data folder. NFS should solve that problem as it allows hardlinking.~~

~~If the containers start throwing errors, run "exportfs -au" & "exportfs -a" or possibly just "exportfs -r" as root on Enterprise to restart the NFS shares, then restart the arr-stack on gallifrey.~~

Switching back to SMB for now because NFS kept throwing "Stale file handle" errors from within the docker containers. Currently have hardlinks enabled inside the *arr settings but can disable them if they cause problems.

I would like to switch back to NFS if possible because it handles file permissions better (and has support for hardlinks), but I haven't solved the problem with docker containers accessing the shares.

### SMB
- Tardis main directory (in /mnt and /home/race)
### NFS - when permissions need to match
- Nextcloud data directory
- Backups (for borgbackup)
