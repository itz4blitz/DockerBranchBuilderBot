# DockerBranchBuilderBot 🤖
![GitHub last commit](https://img.shields.io/github/last-commit/itz4blitz/DockerBranchBuilderBot.svg) ![GitHub stars](https://img.shields.io/github/stars/itz4blitz/DockerBranchBuilderBot?style=social)

![DockerBranchBuilderBot](https://some-imagelink.com/dockerbot.png)

## Description 📋

This script automates the build and push process for multiple branches of Docker images across multiple repositories.

## Table of Contents 📚

- [Requirements](#requirements-)
- [Setup](#setup-)
  - [Adding Multiple Repositories](#adding-multiple-repositories-)
- [Usage](#usage-)

## Requirements 🛠

- Docker 🐳
- Git 📦
- Curl 🌐
  
<a href="https://docker.com"><img src="https://cdn-icons-png.flaticon.com/512/919/919853.png" width="50" height="50"></a> <a href="https://git-scm.com"><img src="https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png" width="50" height="50"></a> <a href="https://curl.se/"><img src="https://curl.se/logo/curl-logo.png" width="50" height="50"></a>


## Setup 🔧

1. **Clone the Repository**

    ```bash
    git clone https://github.com/yourusername/DockerBranchBuilderBot.git
    ```

2. **Configure Script**

    Open the script and update the following:

    - `SLACK_WEBHOOK_URL`: Your Slack webhook URL
    - `USERNAME`: Your GitHub Container Registry username
    - `GHCR_PAT`: Your GitHub Personal Access Token

### Adding Multiple Repositories 📦

To add multiple repositories, ensure they all exist within the same directory. You will then modify the `Main Execution` section of the script to include multiple calls to `process_repo`.

```bash
while true; do
    process_repo "/path/to/your/first/repo" "first_app_name" first_app_branches[@]
    process_repo "/path/to/your/second/repo" "second_app_name" second_app_branches[@]
    sleep 60
done
```

For each repository, you need to:

- Update the `REPO_PATH` and `IMAGE_NAME` to the local path of your Git repository and the name you want to give to the Docker image.
- Update the `app_branches` array to include the branches you wish to build. You can also use regex for branch patterns.
