<b>About this Stylebook</b>

This Stylebook contains everything you need to configure basic EPA checks on Citrix ADC.


<br>
<b>Prerequisites</b>

- Citrix ADC advanced edition with firmware 13.1 or newer 
- Configured Citrix Gateway VServer 
- An installed CA certificate on this ADC in case of device certificate verification

<br>

<b>General information</b><br>
You can combine any of these checks to create your EPA action.

<b>Do you want to allow only specific MAC addresses?</b><br>
Activate this option if you want to do a mac-address verification. Input is in format: 1A-2B-3C-4D-5E-6F
At the moment a maximum of 3000 mac-addresses is supported by this stylebook
<br>

<b>Would you like to scan for running AV Software?</b><br>
This options enables common AV scan. An antivirus software needs to installed and realtime protection feature needs to be enabled (tested with AVG free AV).
<br>

<b>Would you like to scan for running Firewall Software?</b><br>
Activate this option to scan for a running generic firewall. Even Windows defender will be considered.
<br>

<b>Do you want to allow only specific Client Operating Systems?</b><br>
Choose from the list the allowed ones to connect to your network. Only windows systems are considered.
<br>

<b>Do you want to activate device certificate verification within EPA?</b><br>
If you decide to allow access only to systems with a valid device certificate, choose this option.
Please be aware, that the user needs either local admin permissions on the client device, or the SSLVPN plugin needs to be installed. This is the only way to access the device certificate store.


<br>
<b>Manual steps after running the Stylebook</b>

Because I don't want to break any running configuration on the ADC, there are some last manual steps to do: 
- Bind the new created EPA action to your Authentication VServer.
- In case of device certificate verification
	- Bind the CA Root certificatate (and intermediate certificate if present) to your gateway vserver
	- Bind the CA Root certificatate (and intermediate certificate if present) to the "CA for Device Certificate" section within gateway VServer. DO NOT check the box next to "Enable device certificate"
	- Bind the CA Root certificatate (and intermediate certificate if present) to the "CA for Device Certificate" section within aaa VServer.
	
More information you can find here:<br>
https://docs.citrix.com/en-us/citrix-gateway/current-release/vpn-user-config/endpoint-policies/device-certificate-in-nfactor-as-an-epa-component.html
