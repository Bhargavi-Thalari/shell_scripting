# GitHub User Access Report using Shell Script

A beginner-friendly DevOps project that automates the process of listing users who have **read access** to a GitHub repository using the **GitHub REST API**, **Bash Shell Scripting**, and **jq**.

---

##  Project Overview

Managing repository permissions is an important task in DevOps. Manually checking who has access to a GitHub repository can be time-consuming, especially when working with multiple repositories.

This project automates that process by:

- Authenticating with GitHub using a Personal Access Token (PAT)
- Calling the GitHub REST API
- Fetching the list of repository collaborators
- Filtering users who have **read (pull)** access
- Displaying only the GitHub usernames

---

##  Features

- Lists users with read access to a GitHub repository
- Uses GitHub REST API
- Authentication using GitHub Personal Access Token (PAT)
- Parses JSON responses using `jq`
- Beginner-friendly DevOps automation project
- Easy to execute from the Linux terminal

---

##  Technologies Used

- Bash Shell Scripting
- GitHub REST API
- Linux (Ubuntu/Kali)
- curl
- jq

---

##  Project Structure

```text
github-user-access-report-shell-script/
│
├── list_users.sh
├── README.md
└── screenshots/
    ├── without-jq.png
    ├── with-jq.png
    └── output.png
```

---

##  Prerequisites

Before running the script, install the required packages.

### Install jq

```bash
sudo apt update
sudo apt install jq
```

### Generate GitHub Personal Access Token (PAT)

Generate a GitHub Personal Access Token with the required repository permissions.

---

##  Environment Variables

Export your GitHub username and Personal Access Token.

```bash
export username="YOUR_GITHUB_USERNAME"
export token="YOUR_GITHUB_PERSONAL_ACCESS_TOKEN"
```

Example:

```bash
export username="Bhargavi-Thalari"
export token="ghp_xxxxxxxxxxxxxxxxx"
```

---

##  Running the Script

Make the script executable.

```bash
chmod 777 list_users.sh
```

Execute the script.

```bash
./list_users.sh <RepositoryOwner> <RepositoryName>
```

Example:

```bash
./list_users.sh Bhargavi-Thalari aws-ci-demo
```

---

#  Why is `jq` Used?

The GitHub API returns data in **JSON format**. Without processing the JSON, the output contains a large amount of information such as user IDs, profile URLs, avatars, permissions, and many other fields.

Example API response (simplified):

```json
[
  {
    "login": "Bhargavi-Thalari",
    "id": 123456,
    "avatar_url": "...",
    "permissions": {
      "pull": true,
      "push": true
    }
  }
]
```

To display only the usernames of users with **read (pull)** access, the script uses the following command:

```bash
jq -r '.[] | select(.permissions.pull == true) | .login'
```

### Explanation

- `.[]` → Iterates through each collaborator returned by the GitHub API.
- `select(.permissions.pull == true)` → Filters only users who have **read (pull)** permission.
- `.login` → Extracts only the GitHub username.
- `-r` → Prints the output as plain text instead of JSON strings.

Using `jq` makes the output clean, readable, and focused on the required information.

---

#  Project Workflow

```text
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
```

---

#  Demo

##  Output Without Using `jq`

The GitHub API returns the complete JSON response, which contains a lot of information that is not required for this project.

![Output Without jq](output-without-jq.png)

---

##  Output After Using `jq`

Using `jq`, the JSON response is filtered to display only the usernames of users who have **read access** to the repository.

![Output With jq](outPut.png)

#  Sample Output

```text
Listing users with read access to Bhargavi-Thalari/aws-ci-demo...
Users with read access to Bhargavi-Thalari/aws-ci-demo:
Bhargavi-Thalari
```

---

#  Learning Outcomes
Through this project, I learned:
- Writing Bash shell scripts
- Working with GitHub REST APIs
- Authenticating using GitHub Personal Access Tokens (PAT)
- Parsing JSON responses using `jq`
- Linux command-line automation
- Automating repetitive DevOps tasks



