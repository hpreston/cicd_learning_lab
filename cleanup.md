## CleanUp - Uninstall your Application

In this lab we built and put to use a full CICD pipeline for a very simple application.  Full production applicaiton pipelines are more involved with a greater amount of testing to ensure only good code is deployed, but the basic steps and process are the same.

## Uninstall your application

**_In this step you will be entering several commands in a terminal window.  These need to be run from your local repo directory.  If you followed the directions when cloning the repo locally, this command will place you in the correct directory_**

```
cd ~/coding/cicd_demoapp
```

From the root of your code repository...

1. Execute the uninstallation script.
    ```
    $ ./app_uninstall.sh

    # You will be prompted to enter the information needed before the applicaiton deploys.
    # The process will look like this

    Please provide the following details on your lab environment.

    What is the address of your Mantl Control Server?
    eg: control.mantl.internet.com
    control.mantl.domain.com

    What is the username for your Mantl account?
    admin

    What is the password for your Mantl account?

    What is the your Docker Username?
    hpreston

    Uninstalling the demoapp at class/hpreston
    {"version":"2016-07-01T13:26:43.421Z","deploymentId":"731e0df3-056c-4340-ae03-f5155a5e3b50"}

    ```

2. The application has now been destroyed.  

## Wasn't that Fun?

