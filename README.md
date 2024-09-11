# Microsoft Fabric & Power BI: Unlocking the Power of OneLake Shortcuts
 Welcome to this guide on leveraging the power of OneLake shortcuts in Power BI. In this tutorial, we'll explore how to create "shadow shortcuts" for any data source within your Power BI semantic model, making it accessible in OneLake.
# Table of Contents
- [Introduction](#introduction)
- [Setting Up Your Environment](#setting-up-your-environment)
- [Creating and Exporting Data](#creating-and-exporting-data)
- [Enabling OneLake Integration](#enabling-onelake-integration)
- [Exporting Tables to Delta Format](#exporting-tables-to-delta-format)
- [Creating Shortcuts in OneLake](#creating-shortcuts-in-oneLake)
- [Automatic Data Synchronization](#automatic-data-synchronization)
- [Use Cases and Applications](#use-cases-and-applications)
- [Conclusion](#conclusion)

## Introduction
OneLake shortcuts in Power BI enable you to create connections to various data sources, including SQL Server, Excel files, and even DAX-calculated tables. This guide will walk you through the process of creating these shortcuts, exporting your tables to Delta format, and synchronizing your data across your Power BI semantic model and OneLake.

## Setting Up Your Environment
Before you begin, ensure that your Power BI workspace is Fabric-enabled. Your workspace should be either part of the Fabric capacity (F SKU) or one of the Power BI Premium P SKUs (P1, P2, etc.).

## Creating and Exporting Data
Start by preparing a Power BI report that contains data from multiple sources, such as SQL Server and Excel. You can also create tables manually using the "Enter Data" option or by defining DAX-calculated tables within your report.

Once your report is ready, publish it to your Power BI workspace.

## Enabling OneLake Integration
Access Settings: In your Power BI workspace, click the three dots next to your semantic model and select "Settings."
![semantic model setting](https://github.com/user-attachments/assets/b4cc1229-4483-4c9a-b4e7-c9ef24b54bfe)

Enable OneLake Integration: Scroll down to find the "OneLake Integration" option. Enable it and apply the changes. This allows your semantic model to export tables as Delta tables in OneLake.
Admin Portal Settings: In the Power BI Admin Portal, ensure the following settings are enabled under Integration Settings:

![Admin Portal Settings](https://github.com/user-attachments/assets/e3bf0c58-cb31-4e66-8f20-ff5880f5dbb0)

"Semantic model can export data to OneLake"
"Users can store semantic model tables in OneLake"

## Exporting Tables to Delta Format
Connect to your Power BI workspace using SQL Server Management Studio (SSMS) and execute an XMLA query to export your tables to Delta format. This will store your tables in OneLake, making them accessible for further analysis.

{  
 "export": {  
   "layout": "delta",
   "type": "full",  
   "objects": [  
     {  
       "database": "<database name>"  
     }  
   ]  
 }  
}

![OneLake Shortcut](https://github.com/user-attachments/assets/6be521c4-750d-4aa8-96b4-ddaf965f53d2)


## Creating Shortcuts in OneLake
Access OneLake: Navigate to OneLake File Explorer and right-click to sync from OneLake.
Create Shortcuts: Within your Lakehouse, create shortcuts to the exported Delta tables. You can select specific tables or import all tables from your semantic model.
Automatic Data Synchronization

![shortcut to sementic model](https://github.com/user-attachments/assets/febb8c83-b5c2-4747-b9dc-cf360c62b1c3)


After creating shortcuts, any changes to your Power BI semantic model will be automatically reflected in OneLake. For example, if you add a new value to a manually created table in Power BI and publish the report, OneLake will automatically sync the changes.

## Use Cases and Applications
OneLake shortcuts open up a wide range of possibilities, such as:

![possibilities of shortcut](https://github.com/user-attachments/assets/e0768555-d0b8-4189-bc33-5a019669b204)


Reusing data from large SQL Server tables already in your Power BI semantic model.
Sharing DAX-calculated tables across your organization without recreating logic.
Integrating OneLake with your existing data workflows for seamless data management.

## Conclusion
OneLake shortcuts for Power BI semantic models provide powerful new capabilities for data management and collaboration. By following this guide, you can streamline your data workflows and unlock new opportunities for analysis within your organization.
