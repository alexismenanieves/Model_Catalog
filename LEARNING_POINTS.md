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

# Matplotlib
- To see points as circles without fill, use fc='none' and ec='your_color', or alternatively c='None' and edgecolor='C1' [9]

# AWS
- To use the CLI: Retrieve your AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY and AWS_SESSION_TOKEN. Then in the terminal, type export AWS_ACCESS_KEY_ID="my_key_id", export AWS_SECRET_ACCESS_KEY="my_secret_acces" and export AWS_SESSION_TOKEN="my_session_token"
- To list current buckets type: aws s3 ls 
- To list Cloud9 environments: aws cloud9 list-environments --region us-east-1
- To list Cloud9 users in an specific environment: aws cloud9 describe-environment-memberships --environment-id my_env_id --region us-east-1
- To add Cloud9 users to an specific environment: aws cloud9 create-environment-membership --environment-id my_env_id --user-arn "arn:aws:sts::a_id:assumed-role/a_company_id/a_person_id_mail" --permissions "read-write" --region us-east-1
- Amazon Inspector examines the security metrics that compose the National Vulnerability Database (NVD) (https://nvd.nist.gov/vuln ) base score for the vulnerability and adjusts them according your compute environment. The Amazon Inspector score helps you prioritize your findings by highlighting the most critical vulnerabilities for your specific environment. This score is in CVSS format and is a modification of the base Common Vulnerability Scoring System (CVSS) (https://www.first.org/cvss/ ) score provided by NVD.

# References
[1] https://www.tecmint.com/download-and-extract-tar-files-with-one-command/
[2] https://stackoverflow.com/questions/37453841/download-a-file-from-google-drive-using-wget
[3] https://www.howtogeek.com/409115/how-to-delete-files-and-directories-in-the-linux-terminal/
[4] https://linuxconfig.org/how-to-extract-tar-file-on-linux
[5] https://stackoverflow.com/questions/3331337/autotools-tar-this-does-not-look-like-a-tar-archive
[6] https://phoenixnap.com/kb/ubuntu-list-installed-packages
[7] https://www.geeksforgeeks.org/how-to-run-bash-script-in-python/
[8] https://docs.teradata.com/r/Teradata-Tools-and-Utilities-Access-Module-Reference/July-2017/Teradata-Access-Module-for-Amazon-S3/The-config-and-credentials-Files
[9] https://stackoverflow.com/questions/63894301/how-to-get-markers-with-no-fill-from-matplotlib-3-3-1