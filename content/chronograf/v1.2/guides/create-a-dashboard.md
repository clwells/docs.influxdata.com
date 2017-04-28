---
title: Create a Dashboard
menu:
  chronograf_1_2:
    weight: 0
    parent: Guides
---

Chronograf offers a complete dashboard solution for visualizing your data and monitoring your infrastructure.
Use Chronograf's [pre-created dashboards](/chronograf/v1.2/troubleshooting/frequently-asked-questions/#what-applications-are-supported-in-chronograf) or create customized dashboards to meet your setup's needs.
This guide introduces Chronograf's customized dashboard features.

By the end of this document, you'll be aware of all the tools you need to create a dashboard similar to this:

TODO: IMAGE (show all graph types)

## Requirements

This guide assumes you have a working Chronograf instance that's connected to an InfluxDB source.
It uses data from Telegraf's [system statistics](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/system) input plugin.
See the [Getting Started](/chronograf/v1.2/introduction/getting-started/) guide for step-by-step installation and configuration instructions.

## Build a Dashboard

Before you start, navigate to the Dashboards page and click on the `Create Dashboard` button.
That button takes you to your new dashboard; this is your blank canvas on which you'll create your visualization masterpieces.

### Step 1: Name your dashboard 

Click the `Rename` icon at the top of the page.
Name your dashboard anything you want.
Here, we call it `Chronodash`.

TODO: IMAGE (show top bar and point to rename icon)

### Step 2: Enter cell editor mode

Click on the carrot in the existing cell's top right corner and select `Edit`.
This step takes you to cell editor mode:

TODO: IMAGE (point to extended carrot menu)

### Step 3: Create your query

Click on the blue `Add a Query` button to create and edit an [InfluxQL](/influxdb/v1.2/query_language/) query.
In query editor mode, use the builder to select from your existing data and allow Chronograf to format the query for you.
Alternatively, manually enter and edit a query.
Move seamlessly between using the builder and manually editing the query; when possible, Chronograf automatically populates the builder with the information from your raw query.

Here, we use the builder to generate a query that shows the average idle CPU usage grouped by host (in this case, there are three hosts).
By default, Chronograf shows data from the past 15 minutes.

TODO: IMAGE (highlight the query builder and underline the query)

### Step 4: Choose your visualization type

Chronograf supports several visualization types:

**Line**  
Show time-series in a line graph.

**Stacked**  
Show time-series arranged on top of each other.

**Step-Plot**  
Show time-series in a staircase graph.
 
**SingleStat**  
Show the time-series' single most recent value.
 
**Line+Stat**  
Show time-series in a line graph and overlay the time-series' single most recent value.

Here, we choose the Step-Plot:

TODO: IMAGE (show step-plot)

### Step 5: Save your cell
Click on the green checkmark to save your cell.
Note that Chronograf does not save your cell if you navigate away from this page without clicking that checkmark.

### Step 6: Configure your dashboard

* Rename your cell by clicking on the carrot in its top right corner and selecting `Rename`
* Set the dashboard's auto-refresh interval at the top of the page - the default is every 15 seconds
* Set every cell's time range at the top of the page - the default is the past 15 minutes
* Resize your cell by clicking and dragging its bottom right corner
* Move your cell around by clicking its top bar and dragging it around the page

TODO: GIF (Change time range, resize cell, move cell)

Complete your dashboard by creating, editing, and repositioning more cells! 

## Extra Tips

TODO: list these better and explain

* Fullscreen, how to escape
* graph tips
* query templates
* Template variables (link to guide that I will eventually put together)
* Raw queries - fully qualify the measurement
