# Mobile Wish List

The Wish List mobile app lets you pull catalog data from a web service and save items into a secure wish list area in Cloudant or a local database. This walkthrough will guide you through creating a Cloud Foundry (CF) app, adding a Cloudant database to the app, and binding the app to a starter container image.

## Sign up and log into Bluemix and DevOps
Sign up for Bluemix at https://console.ng.bluemix.net and DevOps Services at https://hub.jazz.net. When you sign up, you'll create an IBM ID, create an alias, and register with Bluemix.

## Make sure a public IP is available in your Bluemix space
This solution requires a free public IP. In order to determine if a public IP is available, you need to find the number of used and your max quota of IP addresses allowed for your space.

To find this information:

1. Log into Bluemix at https://console.ng.bluemix.net.
2. Select **DASHBOARD**.
3. Select the space you where you would like your Wish List app to run.
4. In the Containers tile, information about your IP addresses is listed.
5. Check that the **Public IPs Requested** field has at least one available IP address.

If you have an IP address available, you're ready to start building your Wish List app. If all of your IP addresses have been used, you will need to release one. In order to release a public IP, install the CF IC plugin, which can be found at the website below.

https://www.ng.bluemix.net/docs/containers/container_cli_ov.html#container_cli_cfic_installs

Once installed:

1. Log into your Bluemix account and space.

  `cf ic login`  
2. List your current external IP addresses.

  `cf ic ip list`
3. Release an IP address.

  `cf ic ip release <public IP>`

## Create a Cloud Foundry bridge app
The Cloud Foundry app serves as a bridge app to connect your Cloudant database to the MobileFirst container.

1. From the Bluemix Dashboard, click **Create App**.
2. Select **Web** as your app template.
3. Select **SDK for Node.js**, then click **Continue**.
4. Enter an app name and click **Finish** to create your CF app.

## Add Cloudant service
The Cloudant NoSQL Database stores wish list items that users add from their mobile devices. The following steps show you how to add the Cloudant service to your CF bridge app.

1. From the Bluemix Dashboard, select your Cloud Foundry app.
2. In the app dashboard, click **Add a Service or API**.
3. Click **Cloudant NoSQL DB** from the Data and Analytics section to select the service.
4. (Optional) Change the service name for Cloudant.
5. Click **Create** and then **Restage** the app in the following window to make the Cloudant service available to your app.

## Build a MobileFirst container

IBM Mobile First is a starter container for quick set up of the MobileFirst server needed to begin mobile-app connectivity.
Before you begin, make sure that you have an available public IP address.

1. From the Bluemix Dashboard, click **Start Containers** to show a list of container images.
2. On the Container Images page, select **ibm-mobilefirst-starter**.
3. Enter a **Container name** (e.g. mfpf_starter).
4. In the **Public IP address** field, select an unbound public IP address.
5. Leave the **Public ports** field as the default values, “22/tcp, 80/tcp, 9080/tcp, 9443/tcp”.
6. Expand the **Advanced Options** section to show additional configuration settings.
7. In the **Service binding** section, select your Cloud Foundry app to bind it, along with the Cloudant database, to your container.
8. Click **Create** on the right to build your container from the starter image. After the build completes, you can go to the public IP of the container to start setting up your user access.

## Set up MobileFirst
Once the container has built, you can set up your first user to be able to access the IBM MobileFirst Platform Operations Console.

1. From the Bluemix Dashboard, go to the **Containers** section and click on your new MobileFirst container.
2. Click on the public IP address at the top to access the initial registration page to set up your user account.
3. Set a password and click **Register**. This logs you in and takes you to the IBM MobileFirst Foundation main page.
4. (Optional) Click **Open Console** to manage your MobileFirst server in the Operations Console. In this starter container, the applications and adapters for the Wish List app are already installed for you.

## Wish List mobile app
Install the Wish List app on your mobile device to connect to the MobileFirst Platform server. With the IBM MobileFirst starter container, the adapters needed for the Wish List app are already installed.

### Android
To install the Wish List app on your Android device, download Android Studio to open and run the Android project.
Before you begin, the Android project requires Java JDK 7 or better to compile the source code in Android Studio. If you need to download Java, you can get it from [here](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html).

1. Download and install the Android Studio SDK from http://developer.android.com/sdk/index.html to open the Android project.
2. [Download](https://ibm.box.com/shared/static/qq10p5xhqxdszq1j9fqiuy12wnayadrf.zip) the Android project.
3. Extract the .zip file.
4. In Android Studio, click **Open an existing Android Studio project**.
5. Find and select the extracted project folder and click **Choose**.
6. Connect your Android device to your computer and click **Run** at the top of Android Studio to push the app to your device.
7. Select your device and click **OK** to install the app.
8. When the Wish List app starts on your device, click on the menu button in the upper left to show the options.
9. Click **Settings** to show the server settings.
10. Set the server to your public IP with the 9080 port and click **Save**.
11. Click the menu button again, then click **Wish List** to bring up the login screen.
12. Leave the default values for user and password and click **Login**. On the first login, it adds the user to the Cloudant DB, creating the required tables as needed.
13. (Optional) Pressing the **+** (plus) button allows you to add a new item to the wish list stored on Cloudant, which can be retrieved by any device using the same login username and password.
