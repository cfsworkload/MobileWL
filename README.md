#Mobile Wishlist

The Wishlist mobile app implements functionality to fetch catalog data from a web service and contains a secured wishlist area to save items into a Cloudant or local database.

##Create a Cloud Foundry app
The Cloud Foundry app connects your Cloudant database with your MobileFirst server by binding them to this app.
1. Starting from your Bluemix dashboard, click on **Create App** to start creating your Cloud Foundry app.
2. Click on the **Web** button to select the app type to create.
3. Click on **.js** to select the **SDK for Node.js(TM)** then click **Continue**.
4. Enter an app name then click **Finish** to create the Cloud Foundry app.

##Add a Cloudant DB Service
A Cloudant DB stores wishlist items from users as they add them from their mobile devices. 
1. In your app's Overview, click **Add a Service or API** to get a list of services to add.
2. In the search field, type in **Cloudant** to find the **Cloudant NoSQL DB** service in the Data and Analytics section.
3. Click on **Cloudant NoSQL DB** to select the service.
4. **Optional** Change the Service name for Cloudant.
5. Click **Create** and then **Restage** on teh following window to make the Cloudant service available to your app. 


##Build MobileFirst Container

The ibm-mobilefirst-starter container gives a quick startup of the MobileFirst needed to begin mobile app connectivity. 
Before you begin, make sure that you have an available Public IP address. If you have used your quota of 2 Public IP addresses, unbind a Public IP from one of your other containers. Otherwise, you can request or reuse a Public IP later in the steps.

1. From your Bluemix dashboard, click on the **Start Containers** button at the top to show the list of Container Images.
2. In the Container Images section, find and click on the **ibm-mobilefirst-starter** container image.
3. In the **Container name** field, enter a name. e.g. mfpf_starter.
4. In the **Public IP address** field, select an unbound public IP address. If you do not have an unbound Public IP, and you have reached your limit of allowed Public IPs, select Request and Bind Public IP.
5. The Public ports field should be left as the default value, “22/tcp, 80/tcp, 9080/tcp, 9443/tcp”.
6. Click on the **Advanced Options** section to reveal the section.
7. In the **Service binding** section, select the Cloud Foundry app created earlier.
8. Click **Create** on the right to build your container from the container image. The process to build the container may take a few minutes, but when it is complete you can go to the Public IP that you had set to get to the User Registration page.

##Setup MobileFirst
Once the container is completely built, you will need to setup your first user to be able to access the IBM MobileFirst Platform Operations Console.
1. From your Bluemix dashboard, go to the **Containers** section and click on your new MobileFirst container.
2. Click on the Public IP at the top to access the initial registration page to set a password for your first user.
3. Set a password and click **Register**. This logs you in and takes you to the IBM MobileFirst Foundation main page once the user is created.
4. (Optional)Click on the **Open Console** button to manage your MobileFirst server on the MobileFirst Operations Console. In this starter container, the applications and adapters for the Wishlist app are already installed by default.

##WishList Mobile App
The Wishlist app, installed on your mobile device, connects to the MobileFirst Platform server. With the ibm-mobilefirst-starter container, the adapters required for the Wishlist app are already installed.


###Android
To install the app on your Android device, download Android Studio to open and run the Android project.
Before you begin, the android project requires Java JDK 7 or better to compile the source code in Android Studio. If you require Java, download it from [here](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html).

1. Download and install Android Studio SDK from http://developer.android.com/sdk/index.html to open the Android project.
2. [Download](https://ibm.box.com/shared/static/qq10p5xhqxdszq1j9fqiuy12wnayadrf.zip) the Android project.
3. Extract the .zip file.
4. In Android Studio, click **Open an existing Android Studio project**.
5. Find and select the extracted project folder and click Choose.
6. Connect your Android device to your computer and click the **Run** button at the top of Android Studio to push the app to your device.
7. Select your device and click **OK** to begin installing the app onto the device.
8. When the Wishlist app runs on your device, click on the menu button in the upper left to show the options.
9. Click on **Settings** to show the server settings.
10. Set the server to your Public IP with the 9080 port and click **Save**.
11. Click the menu button again and click **Wish List**  to bring up the Login screen.
12. Leave the default values for user and password and click **Login**. On the first login, it adds the user to the Cloudant DB, creating the required tables as needed.
13. (Optional) Pressing the **+** button allows you to add a new item to the wish list stored on Cloudant which can be retrieved by any device using the same login username and password.


