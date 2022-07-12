# Clone Your Oracle E-Business Suite Environment

## **Introduction**

In this lab, we will use the cloning feature of Oracle E-Business Suite Cloud Manager to clone your Oracle E-Business Suite environment.

Estimated Lab Time: 15 minutes

Watch this short video to preview how to clone Oracle E-Business Suite using cloud manager.

### **Objectives**

-   Cloning your EBS environment
-   Configure Local Host Files for the Cloned Environment and Log in to Cloned Oracle E-Business Suite

### **Prerequisites**

-   Tenancy Admin User
-   Tenancy Admin Password
-   Cloud Manager Admin Credentials

Collapse All Tasks

## Task 1: Access the Clone Environment Page

1.  Navigate to the Cloud Manager Environments page.
2.  From the ebsholenv1 environment page, click **Clone** in the top right.

    ![The content is described above.](media/6647c964947ebd782b75c1fae6197049.png)

    Enter Details (see screenshot and points below)

3.  Enter the following values for the clone details (Note these variables in your key-data.txt):

    a. **Environment Name**: ebsholenv2

    b. **Source Apps Password**: apps

    c. **Source WebLogic Server Password**: welcome1

    d. Then Click **Next**

    ![The content is described above.](media/f45205b52560cffae0408e813c55b5f8.png)

4.  Database Tier: We can leave these values as they are and click **Next**

    ![The content is described above.](media/8624b703c9174c21980403a67f8b642f.png)

5.  Application Tier: Make sure **Start Application Tier** is switched on

    ![The content is described above.](media/04824cd8040f05e68300409db30401b9.png)Now Zones/Actions Click **Edit** And Enter and verify the following values

    a. **Web Entry Type**: New Load Balancer

    b. **Load Balancer Shape**: Select 100Mbps

    c. **Protocol**: https

    d. **Hostname**: ebsholenv2

    f. **Domain**: example.com

    g. **Port**: 443

    h. Click **Save Zone** and **Next**

    ![The content is described above.](media/87bbb10e0dbf329bc36b044502a462c2.png)

6.  Extensibility Options:

    a. Click **Next**

    ![The content is described above.](media/1b89fe670e569437628170cc5807c874.png)

7.  SSH Keys:

    a. Upload your SSH Key on the SSH Page

    ![The content is described above.](media/941d0f6e8d0b963cf76499535233dcf9.png)

8.  Review:

    a. Review the information and click Submit

    ![The content is described above.](media/48cf517688180bbe5884662534d50fd3.png)

9.  You can check the status of the activity to clone the environment in the Activities page. The new environment is listed on the Environments page.

## Task 2: Configure Local Host Files for the Cloned Environment and Log in to Oracle E-Business Suite

1.  Now click the Cloud Manager Environment: "ebsholenv2"
2.  Then click the arrow next to **Zone: oneclickdemo**
3.  Note the IP address listed at **Web Entry IP:**

![The content is described above.](media/5b214351b5c3705b2430ec8012b7899d.png)

1.  Edit the local hosts file on your laptop and add an entry.

    **For Windows users**

    1.  Navigate to Notepad in your start menu.
    2.  Hover over Notepad, right-click, and select the option **Run as Administrator**.
    3.  In Notepad, navigate to File \> Open.
    4.  Browse to C:\\\\Windows\\System32\\drivers\\etc
    5.  Find the **file hosts**

        ![The content is described above.](media/a7e211893b21943f09b5c10cf15d9979.png)

    6.  In the hosts file, scroll down to the end of the content.
    7.  Add the following entry to the very end of the file: \<ip_address\> ebsholenv2.example.com
    8.  Save the file.

        **For Mac users**

    9.  Open a Terminal Window.
    10. Enter the following command:

        Copysudo vi /etc/hosts

        This will then require your local computer password to edit the file. Enter and you should see a screen similar to the one shown below.

    11. Type 'i' to edit the file.
    12. Go to the last line and add the following entry as show below: \<ip_address\> ebsholenv2.example.com
    13. Once you have finished editing the file hit 'esc' and type ':wq' to save and exit.

        ![The content is described above.](media/4eb828c7fe7cf9f02cc55ac10e19906f.png)

2.  Log in to Oracle E-Business Suite:

    a. From the Cloud Manager environment page. Click the link following **Login Page:**

    ![The content is described above.](media/0127b854a29708d594a67164c89e489c.png)

    b. When prompted, accept the warning concerning the certificate coming from an unauthorized certificate authority as we are using a self-signed certificate. (You will change the certificate with your own when executing this procedure outside of this hands-on lab.)

    c. On this page, you will log in to Oracle E-Business Suite with the credentials you generated in Lab 3, part 3.

    ![The content is described above.](media/bf1ff2fe8e7a7804b295b59fb9b7a8a3.png)

## Acknowledgements

-   **Author:** Quintin Hill, Cloud Engineering
-   **Contributors:**
-   Santiago Bastidas, Product Management Director
-   William Masdon, Cloud Engineering
-   Mitsu Mehta, Cloud Engineering
-   Chris Wegenek, Cloud Engineering
-   **Last Updated By/Date:** Chris Wegenek, Cloud Engineering, September 2021
