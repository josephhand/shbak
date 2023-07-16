# SHBAK: The POSIX Backup Utility

shbak is a simple backup utility to easily create incremental backups of files.

Each time a backup is performed, a checksum is calculated using the fast b3sum
algorithm. If any corruption is detected shbak will prompt the user to wipe the
backups and create a new backup.

## Installation

First, install the dependencies of shbak, if not already installed:

- b3sum
- GNU tar

To install `shbak`, clone this repository and copy the shell script to a
directory in the path, such as  `~/.local/bin`.

## Usage

### Initializing a backup directory

To setup shbak to perform backups, create a directory in an external medium,
such as a USB drive, or external hard drive. Within this directory, create
a file `.targets` and list the absolute paths of directories to be backed up.
Any lines starting with a `#` will be ignored.

### Creating a new backup

To create a new incremental backup, run the following command:

`shbak <path to backup directory>`

### Resetting to a level-0 backup

To reset to a level-0 backup, delete all files in the directory except for the
`.targets` file, and then run shbak to create a new level-0 backup.
Alternatively, to keep the old backups, a new backup directory can be created
and the `.targets` file copied over.
