# vivaldi-profile-backup
Periodically backups Vivaldi's Default profile to Dropbox.

Really, it can be configured to backup just about anything to anywhere, but this is what I built it for.  
It will zip (probably should really use tar.gz instead) the profile and put it in the target directory  
as well as deleting the oldest archives if the backup folder is larger than the defined max size.

## Installation

* `git clone` to a directory.
* `sudo apt install zip`
* adjust `$target` and `$store` variables in `./backup` to reflect your filesystem


## Running

Under systemd, something like
`systemd-run --on-boot=10m --on-unit-active=2h --uid=<<user>> /path/to/vivaldi-profile-backup/backup`
would start it running, and would continue to run it until shutdown. Adding to a startup file may preserve it across boots.  
Or using a dedicated [timer/service](https://wiki.archlinux.org/index.php/Systemd/Timers) would do this too. An example systemd.service/timer is included in the repo.

Sample crontab entry to run twice an hour
`*/30 *  * * *   your_username    ~/path/to/vivaldi-profile-backup/backup`
