## Learning points

# Your current IP
- If you want to view your IP, use api.ipify.org/?format=json

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

# Ubuntu
- To add users >>> sudo adduser user_name
- To list users >>> getent passwd
- To remove users >>> sudo deluser --remove-all-files user_name

# AWS
- To use the CLI: Retrieve your AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY and AWS_SESSION_TOKEN. Then in the terminal, type export AWS_ACCESS_KEY_ID="my_key_id", export AWS_SECRET_ACCESS_KEY="my_secret_acces" and export AWS_SESSION_TOKEN="my_session_token"
- To list current buckets type: aws s3 ls 
- To list Cloud9 environments: aws cloud9 list-environments --region us-east-1
- To list Cloud9 users in an specific environment: aws cloud9 describe-environment-memberships --environment-id my_env_id --region us-east-1
- To add Cloud9 users to an specific environment: aws cloud9 create-environment-membership --environment-id my_env_id --user-arn "arn:aws:sts::a_id:assumed-role/a_company_id/a_person_id_mail" --permissions "read-write" --region us-east-1
- Amazon Inspector examines the security metrics that compose the National Vulnerability Database (NVD) (https://nvd.nist.gov/vuln ) base score for the vulnerability and adjusts them according your compute environment. The Amazon Inspector score helps you prioritize your findings by highlighting the most critical vulnerabilities for your specific environment. This score is in CVSS format and is a modification of the base Common Vulnerability Scoring System (CVSS) (https://www.first.org/cvss/ ) score provided by NVD.
- Create an event from a SecurityHub event aggregated from Inspector:

1. Configure Amazon Simple Notification Service topic
2. Navigate to Amazon SNS. https://us-east-2.console.aws.amazon.com/sns/v3/home 
3. Click Topics in the left navigation.
4. Click Create topic.
5. Select Standard type.
6. For the name, enter "critical-inspector-findings".
7. Leave everything else as is and click Create topic at the bottom of the page. This will create the topic.
8. Subscribe to the topic
9. From the critical-inspector-findings topic page, click Create subscription.
10. On the Create subscription page, under Protocol, select email.
11. On the Create subscription page, under Endpoint, enter your email address that you want to use for this workshop to receive notifications. You can unsubscribe at the end of the workshop.
12. Click Create subscription.
13. Within a couple minutes, you will receive an email at the email address you entered. Confirm the subscription by clicking "Confirm subscription" in the email.
14. Create an EventBridge Rule to send findings to the topic
15. Now that we have subscribed to our SNS topic, we are ready to send findings there. Since we are using Security Hub to aggregate findings from a few different AWS security services, including Inspector, we will create an EventBridge rule for Security Hub events. To do this, we will create an EventBridge rule, that matches Security Hub events for HIGH and CRITICAL severity findings from Amazon Inspector.

16. Navigate to Amazon EventBridge. https://us-east-2.console.aws.amazon.com/events/home 
17. Click Create rule.
18. On the Define rule detail page, name your rule "critical-inspector-findings".
19. Click Next.
20. On the Build event pattern page, in the Event pattern section, click Edit pattern.
21. Input the following Event Pattern:
```json
{
  "source": ["aws.securityhub"],
  "detail": {
    "findings": {
      "ProductName": ["Inspector"],
      "Severity": {
        "Label": ["HIGH","CRITICAL"]
      }
    }
  }
}
```
22. Click Next.
23. On the Select target(s) page, from the Select a target dropdown, select SNS topic.
24. Then from the Topic dropdown, select critical-inspector-findings.
25. Click Next.
26. On the Configure tags - optional page, click Next.
27. On the Review and create page, click Create rule.

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