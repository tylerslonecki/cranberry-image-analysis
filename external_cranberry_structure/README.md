
To launch a pre-configured jupyter notebook version of this pipeline, click on "Launch Binder"

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/tylerslonecki/cranberry-image-analysis/main?labpath=external_cranberry_structure%2FInternal_Scans.ipynb)


# Docker Environment Setup

## Step 1: Install Docker

Install Docker according to your operating system's instructions. You can find detailed instructions [here](https://docs.docker.com/engine/install/).

- **Linux/MacOS:**
  Open a terminal.

- **Windows:**
  Open PowerShell (may require administrative privileges).

## Step 2: Pull Relevant Docker Image

Enter the following command to pull the latest Docker image:

```bash
docker pull tjs334/cranberry-external:latest
```
This command will pull down the latest working docker image compatible with this pipeline.

## Step 3: Navigate to the Working Folder

Navigate to the desired working folder, which should contain the python file (.py extension) and image folder to be processed. Note that Docker commands may not work in shared folders like BOX, so it's recommended to copy files locally.

### Two Approaches:

1. Use the terminal `cd` command to navigate to the desired working folder.
2.   - For Windows 10+, use the file explorer to navigate to the working folder, click "File", and select "Open Windows PowerShell" (May require "Open as     Administrator"
     - For MacOS, use Finder to navigate to the working folder, right-click, and select "Open terminal" from the context menu (You may need to hover over "Services" first).

## Step 4: Run Docker Container

Once in the correct working folder, enter the following command in your terminal or PowerShell:

```bash
docker run -it -v .:/home/mambauser/ cranberry-external:latest
```


## Step 5: Stop and remove docker container
When you are done, you can stop and remove all docker containers using these commands in your terminal. Otherwise, they will continue to run in the background and use your memory (The images will remain pulled down from Dockerhub)

NOTE: You may need type "exit" into your terminal to leave the container session before entering these commands.
```bash
docker stop $(docker ps -q)
docker rm $(docker ps -a -q)
```

## Repeat Steps 3-5 to use the docker container again in the future
