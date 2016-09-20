# vivaldi-profile-backup
Periodically backups Vivaldi's Default profile to Dropbox.

Really, it can be configured to backup just about anything to anywhere, but this is what I built it for.  
It will zip (probably should really use tar.gz instead) the profile and put it in the target directory  
as well as deleting the oldest archives if the backup folder is larger than the defined max size.
