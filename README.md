# CICD Learning Lab

Here are links to each part of the lab.  They do build on each other so be sure to go in order.

1. [Environment Prep](environment_prep.md)
2. [Stage 1 - Continuous Integration](cicd_stage_1.md)
3. [Stage 2 - Continuous Delivery](cicd_stage_2.md)
4. [Install the Application](app_install.md)
5. [Stage 3 - Continuous Deployment](cicd_stage_3.md)
6. [Stage 4 - Monitoring and Notify Phase](notify_phase.md)
7. [Bonus - CICD In Action!](bonus.md)
8. [Clean-Up](cleanup.md)

## Introduction

This lab is intended to be an introduction to setting up a very basic CI/CD (Continuous Integration/Continuous Delivery) Pipeline.  There are many different technologies and methods that can be used for CI/CD, in this lab we will use:

* Cisco's Mantl Container Stack - <a href="http://mantl.io" target="_blank">Mantl.io</a> which includes:
  * Docker Container Engine - [Docker](http://www.docker.com)
  * Mesos Scheduler - [Mesos/Marathon](http://mesos.apache.org)
* Development Language - Python and Flask
* Source Control - [github.com](https://github.com)
* Container Registry - [hub.docker.com](http://hub.docker.com)
* CICD Server - [drone.io](http://drone.io)
* Notifications - [CiscoSpark.com](http://CiscoSpark.com)

# Prerequisites

To run through this lab, you will need to have accounts (all free) created with the following services, as well as a set of tools properly setup on your laptop or workstation.

## Accounts

* [github.com](https://github.com)
* [hub.docker.com](http://hub.docker.com)
  * **Note: if you are using 2FA for your docker account, let the admin know, as that will change how you do authentication later in the lab exerices.
* [CiscoSpark.com](http://CiscoSpark.com)
  * You will also use your Spark login to retrieve the Spark API token. Go to [developer.ciscospark.com](http://developer.ciscospark.com), where you will find your token by logging into the developer portal, clicking on your image in the upper right corner, and clicking **Copy**
    ![Spark Token](images/spark_token.png)

## Laptop or Workstation

There is no direct requirement for a particular Operating System to be used.  Windows, Mac, or Linux should all work as long as the following software is available.

**_Note: Several of the commands and scripts in the lab involve executing bash commands.  These will work natively on a Mac or Linux machine.  On Windows you'll need to have bash tools installed.  In future updates, alternative commands using PowerShell may be added._**

* git
  * command line tools required
  * GUI clients optional
  * Installation Instructions: [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* docker
  * for platforms with native docker available (ie Linux/Mac) having the docker daemon installed and running can be used
  * docker-machine is also fully acceptable for this lab
  * Installation Instructions: [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)
    * Optionally, you can install the full Docker toolbox for [Mac](https://docs.docker.com/v1.10/mac/), [Linux](https://docs.docker.com/v1.10/linux/), or [Windows](https://docs.docker.com/v1.10/windows/)
* Python 2.7
  * Installation Instructions: [https://www.python.org/downloads/](https://www.python.org/downloads/)
  **_Note: If you already have Python 3.x installed, you may still need to install 2.7.
* drone command line tools
  * drone is the CICD tool used for this lab, and the command line tools are used to properly secure the secret information (i.e. userids, passwords) used for all the services utilized
  * _the tools require docker to be installed and working_
  * Installation Instructions: [http://readme.drone.io/devs/cli](http://readme.drone.io/devs/cli)
  * Basic Installation Steps
    * Linux
      * `curl http://downloads.drone.io/drone-cli/drone_linux_amd64.tar.gz | tar zx`
      * `sudo install -t /usr/local/bin drone`
    * Mac
      * `curl http://downloads.drone.io/drone-cli/drone_darwin_amd64.tar.gz | tar zx`
      * `sudo cp drone /usr/local/bin`

## Lab Environment Details

For this lab you will be leveraging a Lab Mantl Instance and Drone Build Server.  Your lab admin will provide the following information.  Make a note of these details as you will need them periodically during the following lab exercises.

* Drone Build Server Address (referred to as DRONE_SERVER)
* Mantl Control Server Address (referred to as "Mantl Control Server")
* Mantl Username 
* Mantl Password
* Mantl Application Domain (referred to as "Lab Application domain")
* Spark RoomId for Notifications (a hash key provided for Spark Room notifications and referred to as SPARK_ROOM)

## Next Step!

Now that you've got all the pre-reqs setup, move onto the next step.

1. [Environment Prep](environment_prep.md)
