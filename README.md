# Test-SPOFileActionsAsServicePrincipal

To ensure proper permission configuration and demonstrate full functionality for uploading files to SharePoint Online and Download files from SharePoint Online, multiple scripts have been developed.
Other file types besides text files are working with this script. The script has been successfully tested with .xlsx files, for example.

##  Prerequisites

The following components and information are required for script execution and to ensure full functionality:

- PowerShell 7: Necessary for utilizing specific parameters within the scripts.
- App Information (TenantID, AppID, ClientSecret): These enable authentication and confirm correct execution with the intended identity.
- Site URL: Required for determining the SiteID.
- Access to the Site or the Global Reader role: Necessary for retrieving the SiteID.
- Document Library Name: This is needed to identify the correct DriveID from the retrieved drives."

##  Description

### Get SiteId

There are two easy methods to determine the SiteID:

Method 1 (for site members):

Simply append _api/site/id to the site's URL. The displayed Edm.Guid is the required SiteID.

Method 2 (for users with Global Reader rights):

Search for the desired site in the SharePoint Admin Portal. The SiteID can be found at the end of the URL for that site after when editing Site Settings.


### Adjusting configuration file

Execution of the first script requires the configuration section 'ServicePrincipal' to be populated with the appropriate values and the 'SiteId' entry to be adjusted. The 'DriveId' will be determined in the next step.

### Get driveId
The script 01_Get-SPOSiteDriveIDs.ps1 outputs all drives and their corresponding IDs for the site specified in the configuration file. The DriveID of the desired drive should be entered into the configuration file.

### Uploading a File

The script 02_Test-SPOFileUploadAsServicePrincipal.ps1 uploads the file test_upload.txt from the files subfolder to SharePoint Online using the configuration file. 
The file will be displayed in SharePoint Online as test.txt.

### Downloading a File

The script 03_Test-SPOFileDownloadAsServicePrincipal.ps1 downloads the file test.txt from SharePoint Online into the files subfolder. 
The downloaded file will be saved in the file system as test_download.txt to avoid confusion with files of the same name.
