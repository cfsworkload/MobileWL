#Mobile Wishlist

The Wishlist mobile app implements functionality to fetch catalog data from a web service and contains a secured wishlist area to save items into a Cloudant or local database. This has real work applications for retail industry use.

##Build MobileFirst Container

The ibm-mobilefirst-starter container gives a quick startup of all the software and services needed to begin mobile app connectivity. Before you begin, make sure that you have an available Public IP address. If you have used your quota of 2 Public IP addresses, unbind a Public IP from one of your other containers. Otherwise, you can request or reuse a Public IP later in the steps.
1. In Bluemix, click on the **Start Containers** button at the top to show the list of Container Images.
2. In the Container Images section, find and click on the **ibm-mobilefirst-starter** container image.
3. In the **Container name** field, enter a name. e.g. mfpf_starter.
4. In the **Public IP address** field, select an unbound public IP address. If you do not have an unbound Public IP, and you have reached your limit of allowed Public IPs, select Request and Bind Public IP.
5. The Public ports field should be left as the default value, “22/tcp, 80/tcp, 9080/tcp, 9443/tcp”.
6. Click Create to build your container from the container image. The process to build the container may take a few minutes, but when it is complete you can go to the Public IP that you had set to get to the User Registration page.

##Setup MobileFirst
Once you the container is completely built, you will need to setup your first user to be able to access
1. Go to the Public IP you had set to the container to access the Set a password for your first user and click Register. This logs you in and takes you to the IBM MobileFirst Foundation main page once the user is created.
2. Click on the Open Console button to manage your MobileFirst server on the MobileFirst Operations Console.
3. In this starter container, the applications and adapters for the Wishlist app are already installed by default.

##WishList App
The Wishlist app installed on your mobile device connects to the MobileFirst server,

###Android
To install the app on your Android device, download Android Studio to open and run the Android project.
1. Download and install Android Studio SDK, http://developer.android.com/sdk/index.html to open the Android project.
2. Download the Android project. <enter project link>
3. Extract the .zip file.
4. In Android Studio, click Open an existing Android Studio project.
5. Find and select the extracted project folder and click Choose.
6. Connect your Android device to your computer and press the green arrow Run button at the top of Android Studio to push the app to your device.
7. When the Wishlist app runs on your device, click on the menu button to show the options.
8. Click on **Settings** and set the server to your Public IP with the 9080 port.
