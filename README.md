# personal-data-backup-pipeline
A data processing pipeline to back up my personal data to the cloud

## The problem at hand
I have piles of backup DVDs and hard drives from previous computers that I would like to archive for safekeeping
so that I can destroy the original storage media. Some of the files need only to be backed up (word documents, etc.)
but others, raw video files especially, will ideally be able to be compressed or converted to a different format
before being archived.

## Use Cases

### Data DVD Backups
I have piles of DVDs that contain backups of raw video files from video projects in high school.  I
would like to be able to load the DVDs into an optical drive and then run a program with some extra
metadata about the source of the information.  In as long as the program takes to read in the files,
the files should be uploaded to a cloud storage device for processing.

On the cloud side, these video files should be individually processed, converted to a more compressed
video format, and then uploaded to some form of an archival storage bucket.

### Regular files
Normal files, such as text files, code files, etc. should be able to be compressed and uploaded as-is,
as a zipfile or .tar.gz archive.

NOTE: What to do with regular files is a less-developed idea ... I'll need to handle this case more
appropriately when I have a better idea of what the data look like.

Some possible considerations:
    * Maybe code (like from college) should be committed and uploaded to a git repository?
    * Perhaps Google Drive would be a more sensible place for many documents than an archival bucket?
    
### Disks worth keeping in their entirety
For disks that are worth keeping in their entirety, it would be nice to be able to quickly and easily
create an ISO or some other form of disk image and have it be uploaded directly to archival storage.

## Design ideas

1. I would like to be able to view the progress of the application by calling a cloud function.
   The returned webpage would display statistics such as the total number of files the application 
   is aware of, the total amount of disk space occupied by the raw, uploaded files, the amount of disk
   space occupied after compression and processing, overall progress, etc.
2. The application should be deployable on push to the github repository.
3. The application should intelligently handle cases where two identical large files (such as video) are provided.
4. If the data-processing component crashes, it should alert me in some way and then, when I restart the process,
   it should be able to pick up where I left off.
5. Progress logging should be posted to a cloud-based logging service.
