# Protecting data

Operating systems and applications can always be reinstalled, but your data is unique, making it the most important thing on your computer or network to protect.

* Set permissions on the data files and folders.
* Some data is confidential; not only do you not want to lose it, you don't want others to even view it without authorisation.
  * Use [removable storage](Using-removable-storage-media.md) for the most sensitive data (such as database and key files for [password managers](Managing-passwords.md)) 
  * [Use file encryption](File-encryption.md)
  * Use disk encryption, for example [Using cryptsetup (Linux)](Using-cryptsetup.md)
* Assume data loss is inevitable. It's not a matter of if, it is a matter of when. You best protect your data with a solid backup strategy.
  * Make a backup of your entire system or synchronise files with a remote system 
  * You can use the backup utility built into Windows (`ntbackup.exe`) for basic backups. You can use Wizard Mode to simplify the process of creating and restoring backups or you can configure the backup settings manually and you can schedule backup jobs to be performed automatically.
  * On Linux you can use [rsync](Using-rsync.md) or [unison](Using-unison.md), and best is to [archive or compress](Archiving-and-compressing.md) it first.
  * If you make a backup of a system for the first time to be able to restore a system from (the whole point of it), test it with an actual restore. Having done so helps staying calm when the shit hits the fan.
* You may wish to [shred and delete data](Shredding-files-and-deleting-data.md) and not have it found by anyone.

