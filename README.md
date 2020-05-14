# Spectrum Virtualize Check (SVCheck)

This tools generates Excel file of Spectrum Virtualize system via REST API calls.



###### Must read

- Python 3 is required
- [Spectrum Virtualize 8.2.1 or newer](http://www-01.ibm.com/common/ssi/ShowDoc.wss?docURL=/common/ssi/rep_ca/2/897/ENUS218-482/index.html&request_locale=en) is required
- Spectrum Virtualize 8.1.3 introduced API access but [does not have the needed API calls to generate the report](https://github.com/IBM/SVCheck/issues/3).
- [requests, openpyxl and pandas modules **must** be installed](https://github.com/IBM/SVCheck/wiki/How-to-install-the-prerequisites) before running this tool
- To generate the Excel any user role is valid for the user on Spectrum Virtualize system
- If a command replies no data it generates an empty sheet in the Excel file
- Excel file and logs are created on ./output/IP_ADDRESS/ directory
- If your password has non ASCII characters do not pass it as OS parameter



###### Return codes

- 0 = Success
- 1 = Generic error
- 2 = Excel write error
- 3 = Command run error
- 4 = Credentials error
- 5 = User role error
- 6 = Cannot reach API port
- 7 = Error loading SV_system class



###### How to use the tool

```shell
usage: SVCheck [-h] -i IPv4_ADDRESS -u USERNAME [-p PASSWORD] [-v] [-V]

optional arguments:
  -h, --help            show this help message and exit
  -i IPv4_ADDRESS, --ip IPv4_ADDRESS
                        IPv4 address of Spectrum Virtualize system
  -u USERNAME, --username USERNAME
                        username of Spectrum Virtualize
  -p PASSWORD, --password PASSWORD
                        password of Spectrum Virtualize
  -v, --verbose         show verbose messages in console
  -V, --version         show program's version number and exit
```

To run not passing the password as parameter:

```shell
$ ./SVCheck -i 192.168.10.100 -u api
Please type the password for user 'api' :

 Welcome Spectrum Virtualize Checker (SVCheck) version 1.0

 It generates an Excel file Spectrum Virtualize system[s] with relevant information of current status using the API

 Please read the README.md file that comes with this tool
 Please check https://github.com/IBM/SVCheck the latest information about this tool

 This tool comes with no warranty of anykind, use at your own risk

Do you want to continue? (y/n): y

2020-04-28 21:52:24,878 INFO:	 Got valid auth token from 192.168.10.100
2020-04-28 21:52:25,272 INFO:	 Completed saving lssystem information into Excel file
2020-04-28 21:52:25,494 INFO:	 Completed saving lsnodecanister information into Excel file
2020-04-28 21:52:25,725 INFO:	 Completed saving lssystemstats information into Excel file
2020-04-28 21:52:26,057 INFO:	 Completed saving lsnodestats information into Excel file
2020-04-28 21:52:26,389 INFO:	 Completed saving lsvdisk information into Excel file
2020-04-28 21:52:26,644 INFO:	 Completed saving lshost information into Excel file
2020-04-28 21:52:26,914 INFO:	 Completed saving lshostcluster information into Excel file
2020-04-28 21:52:27,252 INFO:	 Completed saving lshostvdiskmap information into Excel file
2020-04-28 21:52:27,525 INFO:	 Completed saving lshostclustervolumemap information into Excel file
2020-04-28 21:52:27,829 INFO:	 Completed saving lsvdiskaccess information into Excel file
2020-04-28 21:52:28,190 INFO:	 Completed saving lsvdiskcopy information into Excel file
2020-04-28 21:52:28,493 INFO:	 Completed saving lsportfc information into Excel file
2020-04-28 21:52:28,776 INFO:	 Completed saving lsfcconsistgrp information into Excel file
2020-04-28 21:52:29,081 INFO:	 Completed saving lsiogrp information into Excel file
2020-04-28 21:52:29,441 INFO:	 Completed saving lsmdiskgrp information into Excel file
2020-04-28 21:52:29,753 INFO:	 Completed saving lssystemip information into Excel file
2020-04-28 21:52:30,069 INFO:	 Completed saving lspartnership information into Excel file
2020-04-28 21:52:31,577 INFO:	 Completed saving lseventlog information into Excel file
2020-04-28 21:52:31,577 INFO:	 Succesfully generated ./output/192.168.10.100/SVCheck_192.168.10.100_2020-04-28_21-52-24.xlsx report
```

To run passing the password as parameter:

```shell
$ ./SVCheck -i 192.168.10.100 -u api -p verysecretpass

 Welcome Spectrum Virtualize Checker (SVCheck) version 1.0

 It generates an Excel file Spectrum Virtualize system[s] with relevant information of current status using the API

 Please read the README.md file that comes with this tool
 Please check https://github.com/IBM/SVCheck the latest information about this tool

 This tool comes with no warranty of anykind, use at your own risk

Do you want to continue? (y/n): y
2020-04-28 21:52:24,878 INFO:	 Got valid auth token from 192.168.10.100
2020-04-28 21:52:25,272 INFO:	 Completed saving lssystem information into Excel file
2020-04-28 21:52:25,494 INFO:	 Completed saving lsnodecanister information into Excel file
2020-04-28 21:52:25,725 INFO:	 Completed saving lssystemstats information into Excel file
2020-04-28 21:52:26,057 INFO:	 Completed saving lsnodestats information into Excel file
2020-04-28 21:52:26,389 INFO:	 Completed saving lsvdisk information into Excel file
2020-04-28 21:52:26,644 INFO:	 Completed saving lshost information into Excel file
2020-04-28 21:52:26,914 INFO:	 Completed saving lshostcluster information into Excel file
2020-04-28 21:52:27,252 INFO:	 Completed saving lshostvdiskmap information into Excel file
2020-04-28 21:52:27,525 INFO:	 Completed saving lshostclustervolumemap information into Excel file
2020-04-28 21:52:27,829 INFO:	 Completed saving lsvdiskaccess information into Excel file
2020-04-28 21:52:28,190 INFO:	 Completed saving lsvdiskcopy information into Excel file
2020-04-28 21:52:28,493 INFO:	 Completed saving lsportfc information into Excel file
2020-04-28 21:52:28,776 INFO:	 Completed saving lsfcconsistgrp information into Excel file
2020-04-28 21:52:29,081 INFO:	 Completed saving lsiogrp information into Excel file
2020-04-28 21:52:29,441 INFO:	 Completed saving lsmdiskgrp information into Excel file
2020-04-28 21:52:29,753 INFO:	 Completed saving lssystemip information into Excel file
2020-04-28 21:52:30,069 INFO:	 Completed saving lspartnership information into Excel file
2020-04-28 21:52:31,577 INFO:	 Completed saving lseventlog information into Excel file
2020-04-28 21:52:31,577 INFO:	 Succesfully generated ./output/192.168.10.100/SVCheck_192.168.10.100_2020-04-28_21-52-24.xlsx report
```
