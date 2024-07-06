<html lang="en">
   <head>
    <li><a href="index.html">Home</a></li>
    <li><a 
href="about.html">About</a>: Linux Bash script
    <li><a href="NAME.html">NAME</a>: GODSFAVOUR AKWATA</li>
    <li><a href="emaill.html">Email</a>:   hisbarrytech@gmail.com</li></ul>
<li><a href="USER-NAME.html">Username</a>:   BARRY</li>

</nav>
<header class="GODSFAVOUR AKWATA">
<h1> HNG-INTERNSHIP</h1>
<p>My work on Linux Bash script</p>

   </head>
   <body>

     
**HI I'M *GODSFAVOUR AKWATA***, a DevOps engineer in HNG_TECH. This is an the  article about a task I was given in HNG11 internship, it is about a Linux user creation Bash script. This Bash script, create_users.sh, is designed to automate the process of creating new users and groups on a Linux system based on the information provided in a text file. The script reads the file, creates the users and groups, sets up home directories with appropriate permissions and ownership, generates random passwords for the users, and logs all actions to a log file. Additionally, the generated passwords are stored securely in a separate file. 

<Header> As a DevOps engineer this is how I handle the task 
  
<Body>
  
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





AUTOMATING LINUX USER CREATION WITH BASH SCRIPTING : A STEP-BY-STEP GUIDE 

As a SysOps engineer, one of the most tedious and time-consuming tasks is creating and managing Linux users and groups. With the increasing number of developers and teams, manual user creation can lead to errors, inconsistencies, and security vulnerabilities. To address this challenge, I developed a bash script that automates the process of creating Linux users and groups, making it efficient, secure, and scalable.

The Problem Statement

Imagine you're a SysOps engineer responsible for creating and managing Linux users and groups for a team of developers. You receive a list of usernames and group names, and you need to create each user with a personal group, add them to the specified groups, generate a random password, and log all actions. This task can be daunting, especially when dealing with a large number of users.

The Solution: create_users.sh

To solve this problem, I created a bash script called create_users.sh. This script reads a text file containing usernames and group names, where each line is formatted as user;groups. The script then creates the users and groups, sets up home directories with appropriate permissions and ownership, generates random passwords for the users, and logs all actions to /var/log/user_management.log. Additionally, it stores the generated passwords securely in /var/secure/user_passwords.txt.

How the Script Works

Here's a step-by-step breakdown of how the script works:

Reading the Input File: The script reads the input file, which contains usernames and group names, one per line. Each line is formatted as user;groups, where user is the username and groups is a comma-separated list of group names.
Creating the User's Personal Group: The script creates a personal group for each user, with the same name as the username. This ensures that each user has a unique group for file ownership and permissions.
Creating the User: The script creates the user using the useradd command, specifying the personal group as the primary group.
Adding the User to Groups: The script adds the user to the specified groups using the usermod command. This is done by iterating over the comma-separated list of group names and adding the user to each group.
Generating a Random Password: The script generates a random password for each user using the pwgen command. This ensures that each user has a unique and secure password.
Setting the User's Password: The script sets the user's password using the chpasswd command.
Logging the Action: The script logs all actions to /var/log/user_management.log, including the username, groups, and password.
Storing the Password Securely: The script stores the generated password securely in /var/secure/user_passwords.txt, with each line formatted as user,password.
Benefits of the Script

The create_users.sh script offers several benefits, including:

Efficiency: The script automates the process of creating Linux users and groups, saving time and reducing the risk of human error.
Security: The script generates random passwords for each user, ensuring that passwords are unique and secure.
Scalability: The script can handle a large number of users and groups, making it ideal for large teams and organizations.
Auditability: The script logs all actions to /var/log/user_management.log, providing a clear audit trail of user creation and management.
Conclusion

In conclusion, the create_users.sh script is a powerful tool for automating Linux user creation and management. By leveraging bash scripting, we can simplify complex tasks, reduce errors, and improve security. Whether you're a SysOps engineer, developer, or IT professional, this script is a valuable resource for streamlining user management and improving overall system efficiency.

Learn More about HNG Internship Program

The create_users.sh script was developed as part of the HNG Internship program, which provides opportunities for developers to gain practical experience in DevOps and other areas. If you're interested in learning more about the program, please visit https://hng.tech/hire or https://hng.tech/premium.

           
<h1>  
&copy; AKWATA GODSFAVOUR 
</h1>
</body>
</html>

