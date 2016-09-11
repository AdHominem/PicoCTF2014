## **Problem Set**

I am given a [PCAP file](https://www.cloudshark.org/captures/44e55fba6c1b) with the task to find out who connected to Thyrin Labs VPN with a spoofed IP and find out his real IP and last name.

## **Attempts**

The file contains logins from various people to a social network.

In line 58 192.168.50.4 makes a GET request to a Daedalus server, this is the one we are looking for.
In line 53 we see a warning that this IP is a duplicate, someone is spoofing here.
I note his MAC 08:00:27:2b:f7:02 and use the filter `eth.addr == 08:00:27:2b:f7:02` to find any duplicates.
We see that this MAC was used by someone connecting to a social network with the name John Johnson, using the IP 192.168.50.3.
 
## **Solution**

We have all our data and assemble the flag:  "johnson,192.168.50.4,192.168.50.3"
