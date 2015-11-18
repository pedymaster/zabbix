# SNMP monitoring of VCSA and ESXi
This is a template which can be used to monitor CPU, Memory, Filesystem, etc on VCSA and ESXi.

The template was exported from Zabbix version 2.4.5
Tested with VCSA 6.0.0-3018521

##How to use:
1. Enable SNMP on the VCSA:
  - connect with SSH to the VCSA and execute the following commands:
    - replace <community> with your SNMP-community
    - `snmp.set --communities <community>`
    - `snmp.enable`
	
2. Import the template in Zabbix:
  - connect to your Zabbix Web-GUI and go to Configuration - Templates
  - click on Import
  - choose the file and click on Import
	
3. Add your VMWARE ESX-hosts to Zabbix:
  - connect to your Zabbix Web-GUI and go to Configuration - Hosts
  - for each host: click on Create Host
  - On the host tab:
    - enter a host name 
    - add an SNMP-interface with your ESX-hosts IP and/or hostname
  - On the templates tab:
    - add template "Template SNMP ESX"
  - On the Macros tab:
    - enter macro {$SNMP_COMMUNITY} with <community> as value
  - click Save

4. Wait for the discovery to fire that creates all items, graphs and triggers