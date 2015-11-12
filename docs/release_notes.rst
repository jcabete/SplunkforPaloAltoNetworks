.. _releasenotes:

=============
Release Notes
=============

App v5.0.0
==========

This major release re-architects the Palo Alto Networks App by splitting it
into an App and an Add-on. The `Palo Alto Networks Add-on`_ is included in the
`Palo Alto Networks App`_ and is installed or upgraded automatically with the App.

Review the :ref:`Upgrade Guide <upgrade>` to upgrade to version 5.0.0.

In addition to the new Palo Alto Networks Add-on, this version also has the
following new features:

* New SaaS dashboard with :ref:`sanctioned_saas`
* CIM 4.x compliance
* Optimized Datamodel for better performance and storage efficiency
* Logs are no longer required to be stored in the pan_logs index
* :ref:`Auto update script <contentpack>` for app and threat lookup tables
* New :ref:`panuserupdate` command for User-ID update
* Enhanced :ref:`pantag` command to leverage log data for tags
* Both commands now support Panorama and VSYS targets, and are more effecient and scalable
* Better command documentation
* Changed from CC license to ISC license
* All new documentation website at http://pansplunk.readthedocs.org

.. _Palo Alto Networks Add-on: https://splunkbase.splunk.com/app/2757
.. _Palo Alto Networks App: https://splunkbase.splunk.com/app/491

Add-on v3.5.1
=============

* Add support for PAN-OS 7.0 new fields
* Add hip-match log type from Firewall and Panorama
* Add sourcetype category
* Add Sanctioned SaaS lookup table (see :ref:`sanctioned_saas`)
* Update app_list.csv and threat_list.csv lookup tables with new format and data
* Fix incorrect value in report_id field for Wildfire logs in PAN-OS 6.1 or higher
* Fix src_category field should be dest_category

Add-on v3.5.0
=============

Included with `Splunk Enterprise Security 4`_.

This new Add-on (TA) for Palo Alto Networks supports logs from Palo Alto
Networks Next-generation Firewall, Panorama, and Traps Endpoint Security
Manager. It is CIM 4.x compliant and designed to work with `Splunk Enterprise
Security 4`_ and the `Palo Alto Networks App for Splunk v5`_.

.. _Splunk Enterprise Security 4:
   https://splunkbase.splunk.com/app/263/
.. _Palo Alto Networks App for Splunk v5:
   https://splunkbase.splunk.com/app/491/


Previous Versions
=================

v4.2.2
------
* Fix drilldowns in Wildfire and Content dashboards
* Fix panel in Content dashboard to display correct data


v4.2.1
------
* Fix Wildfire Report downloader and Applipedia New App check
* Fix Wildfire Dashboard Drilldowns
* Fix Threat Details Dashboard datamodel reference
* Fix Endpoint Dashboard would not work on Splunk 6.0.x
* Fix time range inconsistent on Overview Dashboard
* Fix issue where Endpoint Dashboard disappears if Netflow is enabled.


v4.2
----
* New Palo Alto Networks `Advanced Endpoint Protection`_
* Support Palo Alto Networks `PAN-OS 6.1`_

.. _Advanced Endpoint Protection: http://media.paloaltonetworks.com/lp/traps/
.. _PAN-OS 6.1: https://www.paloaltonetworks.com/documentation/61/pan-os/newfeaturesguide.html


v4.1.3
------
* Special commands (panblock, panupdate, pantag) now available from other apps
* Fix issue with unknown lookup errors during search
* Fix issue with meta scope and global namespace


v4.1.2
------
* Fix some Threat dashboard drilldowns
* Fix scope of CIM fields to remove conflict with some apps
* Remove macros from datamodel that were causing slower acceleration

Note: changes to datamodel may require the acceleration to be rebuilt
before data will show up in the dashboards


v4.1.1
------
* Handle new fields in latest PAN-OS syslogs and WildFire reports
* Significant improvements to indexing efficiency
* Improved handling of Dynamic Address Group tagging
* Improvements and minor updates for Splunk 6.1.x
* Fix minor dashboard issues
* Fix minor field parsing issue


v4.1
----
This is a major update. If upgrading from a previous version, please read the Upgrade Notes in the documentation.

* PAN-OS Data model including acceleration
* Data model accelerated dashboards (replaces TSIDX-based dashboards)
* New command: pantag - tag IP addresses on the firewall into Dynamic Address Groups
* IP Classification - add metadata to your CIDR blocks, classifying them as
  internet/external/dmz/datacenter/etc.
* Applipedia change notifications and highlighting - know when Palo Alto
  Networks releases new application signatures and if those applications are
  on your network


v4.0.2
------
* Fix: Overview dashboard optimizations
* Fix: Top Applications panel would sometimes show error
* Fix: Traffic dashboard form filter works


v4.0.1
------
* Fix: Config dashboard shows all events
* Fix: Better handling of navbar changes


v4.0
----
* Splunk 6 support
* Dashboards converted to Splunk 6 SimpleXML, meaning dashboards can now:

  * Print
  * Export as pdf
  * Produce scheduled reports
  * Use pre-populated dropdowns in filters
  * Change using SplunkWeb by editing the panels

* Maps converted to Splunk 6 built-in maps (removes dependencies on other apps)
* Updated navbar including icons and colors


v3.4
----
* NetFlow support using NetFlow Integrator, a 3rd party program from NetFlow Logic

  * New set of dashboards, charts and graphs centered around NetFlow records
    from Palo Alto Networks devices
  * App-ID and User-ID information is available in NetFlow records

Download a 30-day free trial of NetFlow Integrator at https://www.netflowlogic.com/downloads

Steps to configure NetFlow are available in the NetFlow section of the app
documentation and README.


v3.3.2
------
* Fix: URL in WildFire dashboard corrected
* Fix: Overview dashboard colors were gray on some servers, set back to white
* Fix: Corrected description fields in commands.conf that resulted in log errors
* Fix: Corrected sourcetype in inputs.conf.sample


v3.3.1
------
* Fix: App setup screen allows blank values
* Fix: Several GUI fixes and enhancements


v3.3
----
* Malware analysis reports from the WildFire Cloud are dynamically downloaded
  and indexed when a WildFire log is received from a firewall.
* WildFire dashboard

  * Recent WildFire events
  * Graphs of WildFire statistical data
  * Detect compromised hosts using malware behavior to traffic log correlation

Note: Malware analysis report retrieval requires a WildFire API Key from
https://wildfire.paloaltonetworks.com


v3.2.1
------
Bug Fixes:

* savedsearches.conf: changed hard coded index=pan_logs to pan_index in
  scheduled searches. Thanks to Genti Zaimi for finding the issue and
  providing the fix

* pan_overview_switcher_maps.xml: modified geoip search to include localop to
  force the search to run on the searchhead. Thanks to Genti Zaimi for
  identifying the problem and providing the fix