# Environment Prep

With all the pre-reqs completed, you are ready to start the lab.  We'll start by setting up our new application code repo, container repository, and continuous integration server configuration.

## Forking the cicd_demoapp GitHub Repo

1. Log into GitHub and visit the demo app repo [hpreston/cicd_demoapp](https://github.com/hpreston/cicd_demoapp)
2. Click **Fork** to create a copy of the repo in your account
3. Make a local clone of YOUR repo on your laptop
```
# if you don't have a local directory where you keep projects, create one
mkdir ~/coding

# enter this new directory (or where ever you keep your code)
cd ~/coding

# clone your fork of the demo app
# replace USERNAME with your GitHub user name
git clone https://github.com/USERNAME/cicd_demoapp

```

## Create empty Docker Repository for the Application Container

1. Log into [hub.docker.com](hub.docker.com) with your account
2. Click the blue **Create Repository** button in the upper right corner

![Docker Hub New Repo](images/docker_hub1.png)

3. Name the repo _cicd_demoapp_ and provide a short description.

![Docker Hub New Repo](images/docker_hub_new_repo.png)


## Activate the Repo in Drone

1. Make sure the lab administrator has enabled your GitHub account on the lab server.
2. Navigate to the drone server address provided by the lab administrator, and click **Login**.

![Drone Login](images/drone_login.png)

3. Drone uses GitHub for authentication, so you will either be prompted to log into your account, and then authorize drone, or simply authorize drone if you're already logged into GitHub.
4. Once you've logged in, click the **Available Repositories** tab in the upper right corner.

![Drone Repos](images/drone_available_repos.png)

5. Find the _cicd_demoapp_ repo in the list, and click to activate it.  Drone will then setup a WebHook in GitHub to be notified of relevant events, such as as code pushes, automatically.

![Drone Repos](images/drone_active_repos.png)

6. On the **Active Repositories** tab, you should now see the cicd_demoapp.  If you click on it, there should be no builds reported yet.

## Application and Build Secrets File

In order for Drone to be able to do the hard work of testing your application, building a container and publishing it to your registry, notifying your team of status, and deploying the updated code to production, it requires credentials for several systems to act on your behalf.  These details are often referred to as _secrets_ in application development.   As a general rule, you want to protect these details through encryption to maintain their security.  Commiting your passwords to a code repo is never a good idea, but it is especially bad when using a public repo like github.com.

Drone provides a method to create an encrypted file with needed secrets that can be safely included in a code repo.  This is why we installed the drone command line utilities as part of the pre-reqs.

1. The drone utilities on your laptop need to know the address and access information for the drone server you are using.  We use session environment variables for this.
```
# Configure the drone server address,
# Use the address provided by the lab administrator
export DRONE_SERVER=http://DRONE_SERVER
```
2.  Find your personal Drone token by viewing your profile in the drone console.  Click the down arrow next to your picture in the upper right corner and navigate to _Profile_.  Click the button to _Show Token_ and copy the displayed value.
```
# Configure your token
export DRONE_TOKEN=<your token>
```
3. Test the command line tools by listing the repositories configured.  You should see your cicd_demoapp listed like below.
```
$ drone repo ls
hpreston/cicd_demoapp
```
4. Next we will create the clear text version of our secrets file.  This file is only used to build the encrypted version and should **NEVER** be added to or commited to your repo.  A sample template for the secrets file was included in the demo app.  We will copy this file and edit it.
```
cp drone_secrets_sample.yml drone_secrets.yml
```
5. Edit the copied file in whatever IDE or editor you prefer.  You'll need to provide the details on each line of the file.  This is a YML format, so be sure to maintain proper spacing, including a single space after the colon in each line.
```
environment:
  SPARK_TOKEN: <FROM YOUR DEVELOPER.CISCOSPARK.COM ACCOUNT>
  SPARK_ROOM: <EITHER ONE OF YOUR OWN ROOMS, OR A ROOMID PROVIDED BY THE LAB ADMIN>
  DOCKER_USERNAME: <YOUR HUB.DOCKER.COM USERNAME>
  DOCKER_PASSWORD: <YOUR HUB.DOCKER.COM PASSWORD>
  DOCKER_EMAIL: <YOUR HUB.DOCKER.COM EMAIL ADDRESS>
  MANTL_USERNAME: <MANTL USER PROVIDED BY LAB ADMIN>
  MANTL_PASSWORD: <MANTL PASSWORD PROVIDED BY LAB ADMIN>
  MANTL_CONTROL: <MANTL SERVER ADDRESS PROVIDED BY LAB ADMIN>
```

6. Save your secrets file, but do NOT add or commit it to your repo.
7. Run this command to create the encrypted **.drone.sec** file.
```
# Replace USERNAME with your GitHub username
drone secure --repo USERNAME/cicd_demoapp --in drone_secrets.yml
```
8. Add this file to git, commit and push it to GitHub.  When you `git push` you may be prompted for your GitHub credentials, provide them.
```
# add the file to the git repo
git add .drone.sec

# commit the change
git commit -m "Added .drone.sec file"

# push changes to GitHub
git push
```
9. Return to the drone server web interface and look at your repo status.  You should see a build has kicked off.

![Drone Build](images/drone_1st_build.png)


# Prep Complete

We now have prepped our application code repository, docker registry and cicd server.  Continue to CICD Stage 1 to begin building the deployment pipeline.
