## Learning points
# Linux commands
- A tar file (tape archive) is a file that combines multiple files into a single archive (tarball). It preserves file permissions without compression
- To download a file, you can use curl with the following syntax: curl -o output_name -L "urlyouwant" where -o means output [1]
- To download a file from Google Drive, copy the ID and create this url: 'https://drive.google.com/uc?export=download&confirm=yes&id=ID' replacing ID with the one of the original url [2]
- To create a directory, type: mkdir name_of_dir
- To remove a file, type: rm name_of_file but be careful! it won't warn you [3]
- To untar a file, type: tar -xf name_of_tar file [4]
- If you can't untar a file, it could be that the file is not tar. Verify with: head myfile.tar or if it's zipped had myfile.tar.gz, so if you see binary code, it's encoded. If you see text, it's tar [5]
- To list all available packages in apt, use the command: apt list | less, and to see all the installed packages, type: apt list --installed. To list all the upgradable packages, use: apt list --upgradable [6]

# Bash
- To run a .sh script in Python use subprocess library, and call it with subprocess.run(["/path/to/your/shell/script","arguments"], shell=True)
- Common problems with this process is permission denied when invoking the script, so use chmod +x path/to/script. Another problem is OSError [Errno8], so verify that argument shell is true, of if the script lacks of a shebang [7]

# Teradata
- Config files to send to S3: Use a .config file and then define region = us-east-2 (or whatever region you are using) [8] 

# References
[1] https://www.tecmint.com/download-and-extract-tar-files-with-one-command/
[2] https://stackoverflow.com/questions/37453841/download-a-file-from-google-drive-using-wget
[3] https://www.howtogeek.com/409115/how-to-delete-files-and-directories-in-the-linux-terminal/
[4] https://linuxconfig.org/how-to-extract-tar-file-on-linux
[5] https://stackoverflow.com/questions/3331337/autotools-tar-this-does-not-look-like-a-tar-archive
[6] https://phoenixnap.com/kb/ubuntu-list-installed-packages
[7] https://www.geeksforgeeks.org/how-to-run-bash-script-in-python/
[8] https://docs.teradata.com/r/Teradata-Tools-and-Utilities-Access-Module-Reference/July-2017/Teradata-Access-Module-for-Amazon-S3/The-config-and-credentials-Files