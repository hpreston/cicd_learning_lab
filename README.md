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

This lab is to be an introduction to setting up a very basic CI/CD (Continuous Integration/Continuous Delivery) Pipeline.  There are many different technologies and methods that can be used for CI/CD, in this lab we will use:

* Container Stack - <a href="http://mantl.io" target="_blank">Mantl.io</a>
  * Container Engine - [Docker](http://www.docker.com)
  * Scheduler - [Mesos/Marathon](http://mesos.apache.org)
* Development Language - Python and Flask
* Source Control - [github.com](https://github.com)
* Container Registry - [hub.docker.com](http://hub.docker.com)
* CICD Server - [drone.io](http://drone.io)
* Notifications - [CiscoSpark.com](http://CiscoSpark.com)

# Prerequisites

To run through this lab, you will need to have accounts (all free) created with some services, as well as your laptop or workstation properly setup.

## Accounts

* [github.com](https://github.com)
* [hub.docker.com](http://hub.docker.com)
* [CiscoSpark.com](http://CiscoSpark.com)
  * including [developer.ciscospark.com](http://developer.ciscospark.com) token.  Find your token by logging into the developer portal, clicking your image in the upper right corner, and clicking **Copy**
    ![Spark Token](images/spark_token.png)

## Laptop or Workstation

There is no direct requirement for a particular Operating System to be used.  Windows, Mac, or Linux will all work as long as the following pieces of software are available.

**_Several of the commands and scripts in the lab involve executing bash commands.  These will work as designed from a Mac or Linux Machine.  On Windows you'll need the bash tools to be installed.  In future updates, alternative commands using PowerShell will be created._**

* git
  * command line tools required
  * GUI clients optional
  * Installation Instructions: [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* docker
  * for platforms with native docker available (ie Linux/Mac) having the docker daemon installed and running can be used
  * docker-machine is also fully acceptable for this lab
  * Installation Instructions: [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)
* Python 2.7
  * Installation Instructions: [https://www.python.org/downloads/](https://www.python.org/downloads/)
* drone command line tools
  * drone is the CICD tool used for this lab, and the command line tools are used to properly secure the secrets (ie passwords) used for all the used services
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

For this lab you will be leveraging the Lab Mantl Instance and Drone Build Server.  Your lab admin will provide the following information.  Make a note of these details as you will need them during the lab.

* Drone Build Server Address
* Mantl Control Server Address
* Mantl Username
* Mantl Password
* Mantl Application Domain
* Spark RoomId for Notifications

## Next Step!

Now that you've got all the pre-reqs setup, move onto the next step.

1. [Environment Prep](environment_prep.md)
