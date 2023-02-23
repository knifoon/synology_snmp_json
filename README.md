<div id="top"></div>
<br />
<h3 align="center">Synology SNMP data Logging to JSON File</h3>

  <p align="center">
   A simple shell script to collect data from DSM and format and export it as a JSON file.
    <br />
   Based on <a href="https://github.com/kernelkaribou/synology-monitoring">kernelkaribou's synology-monitoring</a>
    <br />
  </p>
</div>

## Setup
> The set up is basically the same so here's kernelkaribou's setup instructions with a few changes.

The script is best suited to run on the NAS itself and highly recommended. It can be ran on another device but the device would need to be able to run shell scripts, able to make SNMP calls such as using snmpwalk and has the [Synology SNMP MIB's](https://global.download.synology.com/download/Document/MIBGuide/Synology_DiskStation_MIB_Guide.pdf) . With minimal configuration, the Synology NAS should be more than capable of capturing this itself.

1. Save the script to a known location on the NAS. For example: `/volume1/Local/Scripts/syno_json.sh` 
2. Modify any other configuration settings, each should have an explanation.
3. On the Synology NAS, Select Control Panel > Terminal & SNMP > SNMP and enable SNMP V1, V2c service. <br> Ensure that you set the community to 'public' in the Synology settings as the `snmpwalk` command is utilizing the `-c public` flag 
4. On the Synology NAS, Select Control Panel > Task Scheduler > Create >> Scheduled Task >> User-defined Script.
5. Give the Task a recognizable name.
6. On the Task Settings, set the Run command to : `bash /path/to/syno_json.sh /path/to/output.json`
7. On the Schedule:

<ul><ul><ul><ul><ul>
  
| <!-- -->  | <!-- --> |
| --: | -- |
| Run on the following days | `Daily`|
| First run time | `00:00` |
| Frequency |  `Every minute` |
| Last run time | `23:59` |

</ul></ul></ul></ul></ul>

> **NOTE:** *The frequency of times it runs within that minute is defined in the script itself*
