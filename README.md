# vivaldi-profile-backup
Periodically backups Vivaldi's Default profile to Dropbox.

Really, it can be configured to backup just about anything to anywhere, but this is what I built it for.  
It will zip (probably should really use tar.gz instead) the profile and put it in the target directory  
as well as deleting the oldest archives if the backup folder is larger than the defined max size.

## Running

Under systemd, something like
	systemd-run --on-boot=10m --on-unit-active=2h --uid=<<user>> /path/to/vivaldi-profile-backup/backup
would start it running, and would continue to run it until shutdown. Adding to a startup file may preserve it across boots.
Or using a dedicated [timer/service](https://wiki.archlinux.org/index.php/Systemd/Timers) would do this too. An example systemd.service/timer is included in the repo.

This is also possible with cron on non-systemd systems, but I don't know anything about that, so I'll leave it up to your Googlefu to work that one out.
