# CiscoLab Sandbox

https://devnetsandbox.cisco.com/RM/Diagram/Index/faeb4ad1-8d72-4793-9f72-8982f2ea42b6

## intro
<pre>
Overview:
The Multi-IOS Cisco Test Network Sandbox provides a developer with an environment to design, develop and test applications across multiple Cisco Platforms. These platforms include anything that can be ran in Cisco VIRL

This sandbox can be used in conjunction with several learning labs available here. This sandbox can facilitate fairly generic testing of development tools like Puppet, Chef, Ansible, and others.

Please refer to virlutils link below, for instructions to execute the following topologies manually:

    8 nodes datacenter
    2 ios router
    9 router mesh
    extranet
    SD-WAN

The platform/versions utilized in above topologies are:

    IOSxrv 9000 (6.5.1)
    NX-OSv 9k (9.2.2)
    CSR1000v (16.9.1)
    IOSv (15.7.3)
    vEdge, vBond, vSmart & vEdge (18.4.1)

Sandbox Information:
After reserving the Multi-IOS Cisco Test Network Sandbox you will receive VPN access information and credentials via email at the start of the reservation. Once connected via software VPN the developer can access the lab's device and server via Telnet/SSH/HTTP.

This sandbox contains two primary devices.

    VIRL Server - a fairly large VIRL server located at http://10.10.20.160
        SSH credentials – virl/VIRL
        VMMaestro credentials – guest/guest
        UWMAdmin credentials – uwmadmin/password

    devbox - a CentOS VM which contains a standardized environment ready for common environments, including python, docker, etc. For complete specs on the tools server, see, or suggestions on how to improve it go here
        SSH Host - 10.10.20.50
        Default Credentials – developer/C1sco12345

Additionally, we've installed packages to get you started quickly.

    virlutils is a devops-style cli for interacting with VIRL. to explore whats possible, we recommend exploring various topologies you can start with by running virl search from the tools server. Once you've found something interesting, go ahead and virl up it.

Lab Architecture: 
Please reference the Multi-IOS Cisco Test Network Sandbox (this page, right) for lab architecture, ip and login information to the sandbox devices. 
</pre>

## VPN Access

<pre>
Software VPN Access to this Lab:
This tab will explain everything you need to know about how to establish a secure software VPN connection to this lab.  A VPN connection is required for you to interact with the systems and devices in this Lab.  You'll also need to have an active reservation for this Lab.

Stuff You Can (and Should) Do Prior to Your Reservation:
In order to establish a software VPN connection to this Lab, you must download and install Cisco's AnyConnect VPN Client software on any system you plan to use to connect to your Lab.  (And it's ok if you don't do  this until after your reservation has started.  It's all good!)  Here's how you download and install AnyConnect:

    Download the Cisco AnyConnect VPN Client software. [](https://developer.cisco.com/site/devnet/sandbox/anyconnect/)
    Installation Guide for Cisco AnyConnect VPN Client software. [](https://devnetsandbox.cisco.com/Docs/VPN_Access/AnyConnect_Installation_Guide.pdf)


Emails You'll Receive:
When your Lab reservation begins, you will receive several emails communicating important information about the status of your Lab.

    The first email is sent to you from the Lab provisioning automation engine, and indicates that resources in your Lab are in the process of being provisioned and tested.  Your Lab is NOT READY yet, but this email will give an estimate of when your Lab will be available.
    The second email will be sent to you when your Lab is fully provisioned, tested and READY for you to connect.  In this email you'll find the  information required by AnyConnect to establish a VPN connection to your Lab (Network IP Address, VPN Username, VPN Password).

Connecting to Your Lab:
Once you receive the email that says your Lab is ready, you can begin the VPN connection process.  Here's how you establish a VPN connection to your Lab.

    AnyConnect VPN Connection Guide.[](https://devnetsandbox.cisco.com/Docs/VPN_Access/AnyConnect_Connection_Guide.pdf)

</pre>