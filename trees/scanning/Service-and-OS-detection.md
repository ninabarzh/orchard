# Service and OS detection

Service and OS detection use different methods to determine the operating system or service running on a particular port.

## Attack tree

    1 Detect OS and services (AND)
    2 Detect services (AND)
    3 Grab banner

## Tools

* [NMap](https://nmap.org/) 

## Examples

<img align="left" src="../assets/images/warning.png">_These are examples for demystification. Do not scan any devices that you do not have explicit permission to scan. If you do not own the devices I strongly recommend you get that permission in writing._   
<br/>
<br/>

Detection of OS and services:
```
# nmap -A 192.168.1.1
```
Standard service detection:
```
# nmap -sV 192.168.1.1
```
A more aggressive service detection can be helpful if there are services running on unusual ports:
```
# nmap -sV --version-intensity 5 192.168.1.1
```
When performing a version scan (-sV), nmap sends a series of probes, each of which is assigned a rarity value between one and nine. The lower-numbered probes are effective against a wide variety of common services, while the higher-numbered ones are rarely useful. The intensity level specifies which probes should be applied. The higher the number, the more likely it is the service will be correctly identified. However, high intensity scans take longer. The intensity must be between 0 and 9. The default is 7. When a probe is registered to the target port via the nmap-service-probes ports directive, that probe is tried regardless of intensity level. This ensures that the DNS probes will always be attempted against any open port 53, the SSL probe will be done against 443, etc.

The lightest version of the service will be much faster as it does not really attempt to detect the service simply grabbing the banner of the open service.

```
nmap -sV --version-intensity 0 192.168.1.1
```

For OS discovery on a windows network, the smb-os-discovery.nse script can be used to discover operating system, computer name, netbios name and domain:

```
# nmap -p 445 --script smb-os-discovery.nse 192.168.1.0/24
```

