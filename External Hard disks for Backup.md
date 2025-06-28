#routine #archival 

## Format
Use exFat for best compatibility between OS

### Allocation size

> [!TIP] Use 128KB

For Mixed File Sizes (Most Common):
- 128KB
- Good balance for documents, photos, videos
- Default setting works well

For Many Small Files:
- 32KB or 64KB 
- Better space efficiency
- Good for documents, code repositories, email archives
- Less wasted space per file

For Large Files Only:
- 256KB or larger 
- Faster performance
- Good for video editing, large backups, media libraries
- More wasted space with small files

## Directory Structure
```
|-- backup
	|-- ratherbecoding
	|-- gamingpcdesktop
	|-- anyothermachine
|-- media
|-- homemedia
|-- archive
```

## Copy commands
### Crossplatform
[freefilesync](https://freefilesync.org/)

### Windows
Use `robocopy`
```cmd
robocopy D:\wedding_photos\ F:\homemedia\wedding_photos\ /COPY:DAT /E /MT:16 /TEE /ETA /LOG:backup.log

/COPY:DAT : copy files with timestamp
/MIR      : mirror directories
/MT       : threads to use
/LOG      : log file
/E : copy subdirectories, even if empty
/TEE : output to console and log file
/ETA : eta of file arriva
```

> [!TIP]
> See `/MIR` option for syncing folders after initial copy.
> 

### Linux 
Use `rsync`

## Error Prevention
- Enable write barriers on Linux
- Use "Safely Remove Hardware" on Windows
- Use "Eject" on macOS

## Performance Optimization
- Avoid filling drive completely (leave 10-15% free)
- Defragment NTFS partitions periodically on Windows