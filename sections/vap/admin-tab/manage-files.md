---
author: Veracity
description: Overview of the Manage Files tab in the admin tab.
---

# Manage Files

Once you have built your report in Power BI, you can upload it into VAP and share access to it with your clients. By default, VAP will use the data sources from the report, but you can override and update them when uploading a file. For details on data sources and security, go [here](../data.md).

Below the "Manage Files" heading (top centre), you can see if your Power BI files are stored in the EU or USA.
Supported file formats are PBIX, PDF, PNG, JPEG, GIF, JSON. If you want to add release notes, upload a JSON file that follows the [Report Release Note template](configure.md).

The "Manage Files" page shows all uploaded files in a table. To sort them by a specific column, select the column. 

In the right corner of each row you can:
* Refresh data (for [refreshable data sources](../data.md)).
* Schedule a data refresh (for [refreshable data sources](../data.md)).
* See history.
* Edit the file, see report ID and dataset ID or file name.
* Delete the file.

The actions above are listed from the first to the last icon from the left.

## To upload a file

To upload a file:
1. Select the **Upload a file** button.
2. Select the **Choose File** button and select the file from your local machine.
3. For Power BI reports, decide on the **Privacy Level**. For details, see the subsection below.
4. Toggle "I accept and understand that I'm responsible for the content I share in my report".
5. In the **Name** field, provide the name for the file. Veracity recommends including in the file name information that would help recognize the latest version of the file, such as, for example, the client's name, the report's date, and the upload date.
6. Optionally, toggle **I am using Azure Analysis Service**. Using this as a data source will load your data significantly faster than from Azure SQL DB. **Before enabling this toggle**, check the prerequisites under <a href="#AAS">'To use Azure Analysis Service as a data source'</a>.
7. Under **Personal data policy**, confirm whether you are uploading personal data. If you upload personal data, you agree to process it according to Veracity DPA (linked in the upload window).
8. If you are using Azure Analysis Service, toggle "I am using Azure Analysis Service".
9. In the right corner, select the **Upload** button.

If you get a warning when VAP checks your report's data sources, follow the troubleshooting recommended in the warning. 

Note that:
* If you are using a database for the first time in VAP, use the icons from the warning message to set the credentials for the database.
* If your data source cannot be automatically refreshed, you can either check whether your data is stored in a [location supporting refreshable data sources](../data.md) or accept the default fix (no automatic data refresh) and do manual data updates by replacing the file with your report.

### To use Azure Analysis Service as a data source
<a id="AAS"></a>
To be able to load data, add a Veracity VAP service account to your Azure Analysis Services Cube for PowerBI:
* If your VAP service URL starts with insight.**dnv**.com, add 'srvPBIAppPBIEProd@dnv.onmicrosoft.com' to your Azure Analysis Services Cube for PowerBI.
* If your VAP service URL starts with insight.**veracity**.com, add 'srvPBIAppPBIEProdVAP@dnv.onmicrosoft.com' to your Azure Analysis Services Cube for PowerBI.

When uploading your report file (step six above), enable 'I am using Azure Analysis Service'.
<figure>
	<img src="assets/aas.png"/>
</figure>

After this, VAP will pass the Veracity user 'GUID' (the unique Veracity user ID) to the 'CustomData' field in your report. The CustomData feature lets you add a Row filter in your Power BI report. Then, your report can control what Power BI data the user can view.

For more information, refer to [Power BI documentation](https://eur01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fpower-bi%2Fdeveloper%2Fembedded%2Fembedded-row-level-security&data=05%7C02%7CMichal.Zieba%40dnv.com%7Cf56e31065363481d6fdc08dbfc95dc7e%7Cadf10e2bb6e941d6be2fc12bb566019c%7C0%7C0%7C638381492816141580%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=l%2FsdbYT6obGcAl6T8ijvWheeWEariONKXRPzvPFYKOE%3D&reserved=0).

### Privacy Level

There are the following privacy levels:
* None - Before this release, it was the default setting.
* Organizational
* Private
* Public

For details on privacy levels, go [here](https://learn.microsoft.com/en-us/power-bi/guidance/powerbi-implementation-planning-security-content-creator-planning#privacy-levels).

Note that privacy levels set in Power BI Desktop are **not transferred** during the upload. However, after uploading the report, you can set data privacy for each data source separately.

#### For organizational privacy level
Suppose the privacy level in Power BI Desktop data source is organizational. In that case, you must also set it on the data source in your service to avoid issues with refreshing the data source. For details, go [here](https://learn.microsoft.com/en-us/power-bi/guidance/powerbi-implementation-planning-security-content-creator-planning#privacy-levels).

### To set a privacy level for a data source

To set a privacy level for a data source, in the Admin Panel > Manage Files, in the row with the name of the report:
1. Select the editing icon.
2. Select the **Load datasource status** button.
3. Select the icon shown below.
4. For each data source, under **Privacy Level**, select a privacy level.

<figure>
	<img src="assets/privacylevel.png"/>
</figure>
