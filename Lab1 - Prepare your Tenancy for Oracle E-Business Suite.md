# Preparing Your Tenancy for Oracle E-Business Suite

## Introduction

In this exercise, you will prepare your Oracle E-Business Suite environment by setting up EBS Cloud Manager authentication with Identity Cloud Service (IDCS).

Estimated Lab Time: 30 minutes

Watch this short video to preview how to prepare your tenancy for Oracle E-Business Suite.

### **Objectives**

-   Setup EBS Cloud Manager Authentication with Identity Cloud Service (IDCS)
-   Create the EBS Cloud Manager Administrators group and user in IDCS
-   Register Oracle E-Business Suite Cloud Manager as a Confidential Application in IDCS

### **Prerequisites**

-   Tenancy Admin User
-   Tenancy Admin Password

Collapse All Tasks

## Task 1: Create the EBS Cloud Manager Administrators group and user in IDCS

1.  As the Tenancy Administrator, log in to the Oracle Cloud Infrastructure console.![The content is described above.](media/ef87b28eb8a09f26d06f4ce614e00ca8.png)
2.  In the Oracle Cloud Infrastructure console menu, under Governance and Administration, navigate to **Identify & Security \> Federation**.![The content is described above.](media/3d11ecf2e869219ad518134874b74a67.png)
3.  Click on OracleIdentityCloudService
4.  Click on the link next to **Oracle Identity Cloud Service Console**.

    ![The content is described above.](media/1ce7f25763f730d234ed06bc59a5d3ac.png)

5.  Login to IDCS with the Tenancy Admin User.
6.  From the IDCS console, create your Oracle E-Business Suite Cloud Manager group:

    a. Click the navigation menu and select **Groups**.

    b. Click the **Add** button.

    ![The content is described above.](media/de948c9c20d19f41e1f2d8586fce4336.png)

    c. In the Add Group dialog box (Step 1: Group Details), supply the following information:

    1.  **Name**: Enter the name idcs-ebscm-grp
    2.  **Description**: Enter a description of your choice.

        ![The content is described above.](media/22a6f25ce4fd997fb71bfd84a469b726.png)

        d. Click **Finish**.

7.  While still in the IDCS console, create your Oracle E-Business Suite Cloud Manager Administrator user:

    a. Click the navigation menu and select **Users**.

    b. Click **Add**.

    ![The content is described above.](media/ffade37cc85feffa85fc409fc9e11806.png)

    c. In the Add User dialog box (Step 1: Add User Details), supply the following information:

    1.  **First Name**: EBS Cloud Manager
    2.  **Last Name**: Administrator
    3.  **User Name**: ebscm.admin@example.com
    4.  **Use the email address as the user name**: Deselect the check box
    5.  **Email**: Use the same email addressed you used when registering.

        ![The content is described above.](media/6c1ba3830ed0553f8c7071f0c63c5690.png)

        d. Click **Next**.

        e. On the Step 2: Assign User to Groups dialog window, select the check box for the group you just created (idcs-ebscm-grp).

        ![The content is described above.](media/bd1c2435aa98c803a9ed913ea95f63d7.png)

        f. Click **Finish**.

8.  From the IDCS console navigation menu, click **Security** to expand the menu. Then click **Administrators**.
9.  On the Administrators page:

    a. Expand the **Application Administrators** section.

    b. Click **Add**.![The content is described above.](media/bab5eb212be19564c4a1f9709ed13a5a.png)

10. In the Add Users to the Administrator Role dialog box, select the check box for the EBS Cloud Manager Administrator (ebscm.admin@example.com).

    ![The content is described above.](media/56718148826e7aa5653e8d9dad187d49.png)

11. Click **OK**.

    Note: The Cloud Manager administrator will register the app as a confidential application in the next section.

12. Log out of the IDCS console by clicking on your user avatar icon at the top right of your screen. Then, click **Sign Out**.

    ![The content is described above.](media/23ba141f567d0bff77304082b89ae325.png)

## Task 2: Register Oracle E-Business Suite Cloud Manager as a Confidential Application in IDCS

Note: The ebscm.admin@example.com performs the tasks in this section.

In this section, you will register the Oracle E-Business Suite Cloud Manager as a Confidential Application.

1.  Open the Welcome email that was received in the previous section.
2.  Click the yellow **Activate Your Account** button in the email.

    ![The content is described above.](media/568c3207f77e693516e4684ad05c52c9.png)

3.  Enter a new password, confirm, and click Submit. Document this password in your key-data.txt, field Cloud_Manager_Admin_Password.
4.  Click **OK** to continue, which will take you to the IDCS Login screen. Otherwise, log into IDCS using the steps outlined previously (OCI Console \> Identity \> Federation).
5.  Enter the EBS Cloud Manager user name (ebscm.admin@example.com) and password you just entered in the previous screen to log in.
6.  Click on your user avatar menu in the top right corner. This will display a drop-down menu.

    ![The content is described above.](media/8c84a7038fd2e0124bd691cecfc315b7.png)

7.  Select **Admin Console**. This will display the IDCS Administration Console.

    If there is no **Admin Console** option to select, you may already be on the Admin Console. Below is an example of the Admin Console after you login.

    ![The content is described above.](media/e7c16e7bd4260be9d9f6a1d8a69ac89e.png)

8.  In the top right of the Applications tile, click the icon to Add an Application.

    ![The content is described above.](media/3f766cb59ac5a015205bc95785041bc3.png)

9.  Select **Confidential Application**. This takes you to the Add Confidential Application page.

    ![The content is described above.](media/60611b2cd5487d5b2caf0791a3773fff.png)

10. On the Details screen, enter the following:

    a. **Name**: Oracle E-Business Suite Cloud Manager

    b. **Description**: Write a description.

    c. Click **Next**.

    ![The content is described above.](media/7f821edc7a720e9add8055014d03e328.png)

11. On the Client screen:

    a. Select **Configure this application as a client now**.

    b. Under **Allowed Grant Types**, select the following check boxes:

    1.  Client Credentials
    2.  Refresh Token
    3.  Authorization Code

        c. Here we are going to set our cloud manager url. For this lab we will use the following example URL.

        Example Cloud Manager URL: https://myebscm.ebshol.org:443

        Save your cloud manager url in your key-data.txt file as Cloud_Manager_URL

        Using the Cloud Manager url you have just saved, append that url with the following values as shown below to enter your Redirect URL.

        d. **Redirect URL**: \<Cloud_Manager_URL\>/cm/auth/callback

        Example: https://myebscm.ebshol.org:443/cm/auth/callback

        e. **Logout URL**: Leave this field empty.

        f. **Post-Logout Redirect URL**: \<Cloud_Manager_URL\>/cm/ui/index.html?root=login

        Example: https://myebscm.ebshol.org:443/cm/ui/index.html?root=login

        g. Select the **Introspect** option for **Allowed Operations**.

        ![The content is described above.](media/3c42c6a23075cf261c06aca59c2f9da2.png)

        h. Under **Grant the client access to Identity Cloud Service Admin APIs**:

    4.  Click Add.

        ![The content is described above.](media/89dcc7fcc5c1c3a105a273fe22641a15.png)

    5.  Select **Authenticator Client** and **Me** in the pop-up window.
    6.  Click Add again.

        ![The content is described above.](media/c2690ec67d0493a43b0d6713edbe30e8.png)

        i. Click **Next** at the top of the screen.

12. On the Resources screen, click **Next**.

    ![The content is described above.](media/dc441eb7fa6e4c64ac308f7e4b5697b0.png)

13. On the Web Tier screen, click **Next**.![The content is described above.](media/376a5205daf5242bad24e3dfccbf8ce7.png)
14. On the Authorization screen, click **Finish**.![The content is described above.](media/5dee199b40bc07877fac061b2088d285.png)
15. Make note of the following values in your key-data.txt file (under Client_ID and Client_Secret, respectively) when they are displayed in a pop-up window:

    a. **Client ID**

    b. **Client Secret**

    ![The content is described above.](media/ae093c168983eb30d92a2bd347cc3ced.png)

    If you need to view these values again, select the **Configuration** tab in the app's page. The values are listed under **General Information**.

    ![The content is described above.](media/798c0cbcf4f7e6db75ff2901dba7cee5.png)

16. Click **Close**.
17. Click **Activate** to activate the Confidential Application.

    ![The content is described above.](media/9369464705004e1e3ff0ad66a3121d8e.png)

18. Click on the avatar icon on the top right hand side of the screen.
19. Select the **About** option.

    ![The content is described above.](media/5d87378c05de1533dabdbc40c6efd661.png)

20. Copy the value displayed for Instance GUID. Record this as Client_Tenant in the key-data.txt. Your IDCS Client Tenant begins with the characters idcs- and then is followed by a string of numbers and letters, for example, idcs-6572bfeb183b4becad9e649bfa14a488.

    ![The content is described above.](media/d435ed57baeecebcd7a35744259d3860.png)

You may now proceed to the next lab.

## Acknowledgements

-   **Author:** Quintin Hill, Cloud Engineering
-   **Contributors:**
-   Santiago Bastidas, Product Management Director
-   William Masdon, Cloud Engineering
-   Mitsu Mehta, Cloud Engineering
-   Chris Wegenek, Cloud Engineering
-   **Last Updated By/Date:** Chris Wegenek, Cloud Engineering, September 2021
