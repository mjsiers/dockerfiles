# SNMP Trap Logging Docker Image

This docker image runs the snmptrapd application in the forground which logs out
all the trap notifications to the console window. This docker image is used
as a verification tool to ensure the SNMP agent is sending the notification messages.

Below is the command that is used to execute the docker image.  It can be terminated 
by using the CTRL-C keyboard sequence in the console window.

## Run Image Command
```docker run -it --rm -p 162:162/udp sas/snmptrapd```

## SNMP V3 Configuration Information
The SNMP V3 user authentication information is contained in the Dockerfile.
It writes the default trap user authentication values into the snmptrapd.conf file.

If these parameters need to be changed, a new docker image will need to be built
using the command listed below.

## Build Image Command
```docker build -t snmp/snmptrapd .```

## Dependancies
This docker image is built of the latest version of the Alpine Linux container.
Execute the following command to fetch the latest version of this container.

```docker pull alpine```
