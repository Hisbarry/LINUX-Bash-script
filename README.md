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
