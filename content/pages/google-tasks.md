---
title: Google Tasks
date: 2021-07-08T18:02:28.476Z
permalink: /site-building/gtm.html
eleventyNavigation:
  order: 100
  key: Google Tasks
  parent: Site Building
---
## Add Google Tag Manager code to Portal

Video walkthrough 
https://share.getcloudapp.com/2Nu00Pvy



1. Sign into https://tagmanager.google.com/#/home with whichever gmail account you’re using.
2. Click **Create Account**.
3. Fill out **Account Setup**, **Container Setup**, and choose **Web**, then click Create.
4. Close pop-up modal and click on **Tags** in right hand column, then click **New**.
5. Click **Tag Configuration**, then choose **Google Analytics: Universal Analytics** from the fly out window.
6. Name Tag Configuration **GA Tag**. Leave **Tracking Type** as **Page View**. Under **Google Analytics Settings**, select **New Variable**. Name variable **GA Code**. Add your site’s Analytics UA code to **Tracking ID** and click save. Click **Triggering** box and select **All Pages**. Now click save at top right of GA Tag window.
7. Click **Submit** at top right of main Tag Manager window. Type *"Added GA Tag"* to **Version Name**, then click **Publish**.
8. Click **Workspace** in topbar. Click blue GTM ID in topbar and copy GTM ID (ex. GTM-K9LX2QV). Paste into **Home » Sites » Domain Management** in Portal under **Analytics/Conversions > Google Tag Manager ID**. Save changes.
9. Done

## GA & GTM for JL & HG* Sites
https://cdn.treehouseinternetgroup.com/cms_images/2714/how-to-set-up-junkluggers-analytics-and-tag-manager%20(1).pdf

*For Hello Garage Sites add 2 Goals to GA - Leads and Bookings. Check out a pre-existing HG site for reference!