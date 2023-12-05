[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/tylerslonecki/binder-test/main?labpath=Internal_Scans.ipynb)


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
docker pull tjs334/micromamba-base-jupyter:latest
```
OR

```bash
docker pull tjs334/micromamba-base-terminal:latest
```
This command will pull down the latest working docker image compatible with this pipeline.

## Step 3: Navigate to the Working Folder

Navigate to the desired working folder, which should contain the Jupyter notebook and image files to be processed. Note that Docker commands may not work in shared folders like BOX, so it's recommended to copy files locally.

### Two Approaches:

1. Use the terminal `cd` command to navigate to the desired working folder.
2. For Windows 10+, use the file explorer to navigate to the working folder, hold shift, right-click, and select "Open PowerShell window here." For MacOS, use Finder to navigate to the working folder, right-click, and select "Open terminal" from the context menu (You may need to hover over "Services" first).

## Step 4: Run Docker Container

Once in the correct working folder, enter the following command in your terminal or PowerShell:

```bash
docker run -it --rm -p 8888:8888 -v .:/home/mambauser/ tjs334/micromamba-base:latest
```
OR

```bash
docker run -it -v .:/home/mambauser/ micromamba-base-terminal:latest
```

## Step 5: Access Jupyter Notebook

Copy the second URL provided in the terminal after running the Docker command and paste it into a browser search bar.

## Step 6: Use Jupyter Notebook

With the correct environment setup, you can use your Jupyter notebook as usual. You should have access to the files in your selected working directory within the Jupyter environment.

![Alt Text](https://github.com/tylerslonecki/bi-image-analysis/blob/main/bi/assets/jupyter_example.PNG)

When you are done, you can stop and remove all docker containers using these commands in your terminal. Otherwise, they will continue to run in the background (The images will remain pulled down from Dockerhub)

NOTE: You may need to press CTRL+C (Windows/Linux) or CMD+C (MAC OS) twice to terminate the process in the terminal before being able to enter these commands.
```bash
docker stop $(docker ps -q)
docker rm $(docker ps -a -q)
```

## Repeat Steps 3-6 to use the docker container again in the future
