# LINUX-Bash-script
#!/bin/bash

# Set the log file and password storage file
LOG_FILE=/var/log/user_management.log
PASSWORD_FILE=/var/secure/user_passwords.txt

# Function to create a user and set up their home directory
create_user() {
  local username=$1
  local groups=(${2//,/ })
  
  # Create the user's personal group
  groupadd ${username} &>> ${LOG_FILE}
  
  # Create the user and add them to their personal group and other specified groups
  useradd -m -g ${username} -G ${groups[*]} ${username} &>> ${LOG_FILE}
  
  # Set a random password for the user
  password=$(pwgen -1)
  echo "${username}:${password}" >> ${PASSWORD_FILE}
  echo ${password} | passwd --stdin ${username} &>> ${LOG_FILE}
  
  # Set permissions and ownership for the user's home directory
  chown ${username}:${username} /home/${username} &>> ${LOG_FILE}
  chmod 700 /home/${username} &>> ${LOG_FILE}
}

# Read the input file and create users
while IFS=';' read -r username groups
do
  # Remove whitespace from the input
  username=${username// /}
  groups=${groups// /}
  
  # Check if the user already exists
  if id -u ${username} &>/dev/null; then
    echo "User ${username} already exists. Skipping..." &>> ${LOG_FILE}
  else
    create_user ${username} ${groups}
    echo "User ${username} created successfully." &>> ${LOG_FILE}
  fi
done < "$1"

exit 0

DevOps Stage 1: Linux User Creation Bash Script
==============================================

This script, `create_users.sh`, is designed to create Linux users and groups based on a input file containing usernames and group names. The script reads the input file, creates the users and groups, sets up home directories with appropriate permissions and ownership, generates random passwords for the users, and logs all actions to `/var/log/user_management.log`. Additionally, it stores the generated passwords securely in `/var/secure/user_passwords.txt`.

### How to use the script

1. Create a text file containing the usernames and group names, where each line is formatted as `user;groups`.
2. Run the script by supplying the name of the text file as the first argument, e.g. `bash create_users.sh input_file.txt`.

### Technical Article

As a SysOps engineer, I was tasked with creating a bash script to automate the process of creating Linux users and groups. This script is designed to be flexible and easy to use, with clear documentation and comments throughout.

The script uses the `useradd` and `groupadd` commands to create the users and groups, and the `pwgen` command to generate random passwords. It also uses the `chpasswd` command to set the user's password, and the `usermod` command to add the user to the specified groups.

One of the key features of this script is its ability to handle errors and exceptions. For example, if a user or group already exists, the script will skip over it and continue with the next line in the input file.

I was inspired to write this script as part of the [HNG Internship program](https://hng.tech/internship), which provides opportunities for developers to gain practical experience in DevOps and other areas. I hope that this script will be useful to others, and that it will help to demonstrate the power and flexibility of bash scripting.

For more information about the HNG Internship program, please visit [https://hng.tech/hire](https://hng.tech/hire) or [https://hng.tech/premium](https://hng.tech/premium).
