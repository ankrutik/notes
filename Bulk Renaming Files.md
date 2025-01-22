#files #utility

# Using Bulk Rename Utility
[Bulk Rename Utility web page](https://www.bulkrenameutility.co.uk/Download.php)

Copy files into folders by count. For example, video files as per season. In  Windows, select multiple files and use option to "New folder with selection".

In BRU, select files.
Assuming files are named as "Episode 123".
Use following configuration...
- RegExp section
	- `Episode \d*`
	- `S09E`
- Numbering section
	- Mode: Insert
	- At: 4
	- Start: 1
	- Increment: 1
	- Pad: 2