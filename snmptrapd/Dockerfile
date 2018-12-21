FROM alpine:latest

# install the required utilities
RUN apk --no-cache add bash net-snmp net-snmp-tools

# setup the snmptrapd configuration file with V3 user authentication information
RUN echo 'disableAuthorization yes' > /etc/snmp/snmptrapd.conf
RUN echo 'createUser -e 0x6794701964 trapuser MD5 authsecret DES privsecret' >> /etc/snmp/snmptrapd.conf
RUN echo "authUser log trapuser" >> /etc/snmp/snmptrapd.conf
RUN echo "authCommunity log public" >> /etc/snmp/snmptrapd.conf

# configure snmp to load custom MIB file(s)
#COPY CUSTOM-MIB.txt /usr/share/snmp/mibs/.
#RUN echo 'mibs +CUSTOM-MIB' > /usr/share/snmp/snmp.conf

# expose the default port that snmptrapd receives notifications on
EXPOSE 162/udp

# set the startup command for the docker image
#CMD ["bash"]
CMD ["snmptrapd","-L","o","-f"]
