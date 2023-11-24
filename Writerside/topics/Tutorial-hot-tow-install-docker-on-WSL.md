# Tutorial hot tow install docker on WSL

This tutorial will show you how to install and set Docker on WSL.

## Prerequisites

Use Windows 10 or Later.

## Install ubuntu with Windows store

1. Open Windows Store
2. Search for Ubuntu
3. Install Ubuntu
4. Open Ubuntu

## Git configuration on Ubuntu

Git is already installed on Ubuntu, but you need to configure it.

1. Open Ubuntu
2. configure git with your name and email
    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "
    ```
3. Generate a new SSH key
    ```bash
    ssh-keygen
    ```
4. Copy the SSH key to your clipboard
    ```bash
    cat ~/.ssh/id_rsa.pub
    ```
5. Add the SSH key to your GitHub account
    - Go to your GitHub account
    - Click on your profile photo
    - Click on Settings
    - Click on SSH and GPG keys
    - Click on a New SSH key
    - Paste your key into the "Key" field
    - Click on Add an SSH key

## Install Docker on Ubuntu

1. run the following command to install Docker
    ```bash
    # Add Docker's official GPG key:
    sudo apt-get update
    sudo apt-get install ca-certificates curl gnupg
    sudo install -m 0755 -d /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    sudo chmod a+r /etc/apt/keyrings/docker.gpg
    
    # Add the repository to Apt sources:
    echo \
      "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
      "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
      sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt-get update
    ```
2. Install Docker Packages latest version
    ```bash
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugins
    ```

3. check if Docker is installed and running (optional)
    ```bash
    sudo docker run hello-world
    ```
   <note>
        This command is used to check if Docker is installed and running.
        docker downloads the hello-world image and runs it in a container.
   </note>

Congratulations, you have successfully installed Docker on WSL.

Go to [quick starter](QuickStarter.md#run-api-with-docker) to start the api on your Docker.

After you have finished the quick starter, you can go to [Tutorial Postman](TutorialPostman.md) to learn how to use
Postman with Laravel Sanctum.