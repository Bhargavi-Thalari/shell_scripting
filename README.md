# shell_scripting
# GitHub User Access Report using Shell Script
A simple Bash shell script that lists users who have to a GitHub repository using the GitHub REST API.

# Project OverView
Managing repository access is an important part of DevOps. This project automates the process of checking which users have read access to a GitHub repository. The script authenticates using a GitHub Personal Access Token (PAT), fetches the repository collaborators, filters users with read permissions, and displays their usernames.

Features 
- List users with read access to any GitHub repository 
- Uses GitHub REST API
- Authentication using GitHub Personal Access Token
- Parses JSON response using `jq`
-  Easy to run from the Linux terminal
- Beginner-friendly DevOps automation project

Technologies Used

- Bash Shell Scripting
- GitHub REST API
- Linux (Kali/Ubuntu)
- curl
- jq

Project Structure
shell-scripting/
│
├── list_users.sh
├── README.md
└── screenshots/
    ├── setup.png
    └── output.png

Prerequisites
Before running the script, make sure the following tools are installed.
Commands:
  sudo apt update
  sudo apt install jq

Generate GitHub Personal Access Token
Generate a GitHub Personal Access Token (PAT) with the required repository permissions.

Environment Variables
Export your GitHub username and Personal Access Token.
Commands:
  export username="YOUR_GITHUB_USERNAME"
  export token="YOUR_GITHUB_PERSONAL_ACCESS_TOKEN"

Running the Script 
Make the script executable.
Command:
  chmod 777 list_users.sh 

Execute the script.
Command:
  ./list_users.sh <RepositoryOwner> <RepositoryName>

Project Workflow

  User
   │
Run Script
   │
Read GitHub Username & PAT
   │
Accept Repository Owner & Repository Name
   │
Build GitHub API URL
   │
Send API Request using curl
   │
Receive JSON Response
   │
Filter Read Access Users using jq
   │
Display Usernames


