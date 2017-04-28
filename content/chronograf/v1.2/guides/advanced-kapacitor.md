---
title: Advanced Kapacitor Usage
menu:
  chronograf_1_2:
    weight: 60
    parent: Guides
---

Chronograf provides a user interface for [Kapacitor](/kapacitor/v1.2/), InfluxData's processing framework for creating alerts, running ETL jobs, and detecting anomalies in your data.
This guide offers a lower-level insight into how Kapacitor interacts with Chronograf and introduces advanced Kapacitor usage within Chronograf.

### Content

* [TICKscript Management](#tickscript-management)
* [Alert History Management](#alert-history-management)

## TICKscript Management

TODO

## Alert History Management

Chronograf stores the information on the Alert History page as time-series data in InfluxDB.
It stores it in the `chronograf` database and in the `alerts` [measurement](/influxdb/v1.2/concepts/glossary/#measurement).
By default, those data are subject to an infinite [retention policy](/influxdb/v1.2/concepts/glossary/#retention-policy-rp) (RP), that is, InfluxDB stores them forever.
Users who expect to have a large number of alerts and users who do not want to store their alert history forever, may want to shorten the [duration](/influxdb/v1.2/concepts/glossary/#duration) of that RP.

### Modify the RP in Chronograf

Use Chronograf’s Admin page to modify the retention policy in the `chronograf` database.
In the DB Management tab:

#### Step 1: Locate the `chronograf` database and click on the infinity symbol (∞)

![RP in practice](/img/chronograf/v1.2/g-advkap-dur.png)

#### Step 2: Enter a different duration

The minimum allowable duration is one hour (`1h`) and the maximum is infinite (`INF`).
See the InfluxDB documentation for the list of [acceptable duration units](/influxdb/v1.2/query_language/spec/#duration-units).

#### Step 3: Click the green check mark to save your changes

InfluxDB only keeps data in the `chronograf` database that fall within that new duration; the system automatically deletes any data with timestamps that occur before the duration setting.

### Example

If you set the retention policy's duration to one hour (`1h`), InfluxDB automatically deletes any alerts that occurred before the past hour.
Those alerts no longer appear in your InfluxDB instance or on Chronograf's Alert History page.

Looking at the image below and assuming that the current time is 19:00 on April 27, 2017, only the first three alerts would appear in your alert history; they occurred within the previous hour (18:00 through 19:00).
The fourth alert, which occurred on the same day at 16:58:50, is outside the previous hour and would no longer appear in InfluxDB's `chronograf` database or on Chronograf's Alert History page.

![RP in practice](/img/chronograf/v1.2/g-advkap-rp.png)