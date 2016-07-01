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

* Container Stack - Mantl.io
  * Container Engine - Docker
  * Scheduler - Mesos/Marathon
* Development Language - Python and Flask
* Source Control - github.com
* Container Registry - hub.docker.com
* CICD Server - drone.io
* Notifications - CiscoSpark.com

# Prerequisites

To run through this lab, you will need to have accounts (all free) created with some services, as well as your laptop or workstation properly setup.

## Accounts

* github.com
* hub.docker.com
* ciscospark.com
  * including developer.ciscospark.com

## Laptop or Workstation

There is no direct requirement for a particular Operating System to be used.  Windows, Mac, or Linux will all work as long as the following pieces of software are available.

* git
  * command line tools required
  * GUI clients optional
* docker
  * for platforms with native docker available (ie Linux/Mac) having the docker daemon installed and running can be used
  * docker-machine is also fully acceptable for this lab
* Python 2.7
* drone command line tools
  * drone is the CICD tool used for this lab, and the command line tools are used to properly secure the secrets (ie passwords) used for all the used services
  * the tools require docker to be installed and working
  * [http://readme.drone.io/devs/cli](http://readme.drone.io/devs/cli)
  * Basic Installation Steps
    * Linux
      * `curl http://downloads.drone.io/drone-cli/drone_linux_amd64.tar.gz | tar zx`
      * `sudo install -t /usr/local/bin drone`
    * Mac
      * `curl http://downloads.drone.io/drone-cli/drone_darwin_amd64.tar.gz | tar zx`
      * `sudo cp drone /usr/local/bin`

## Next Step!

Now that you've got all the pre-reqs setup, move onto the next step.

1. [Environment Prep](environment_prep.md)
