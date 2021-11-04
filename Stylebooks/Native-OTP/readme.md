<b>About this Stylebook</b>

This Stylebook contains everything you need to configure Native OTP Feature of Citrix ADC.
Native OTP is the Citrix ADC built in OTP solution which includes a self service portal. The number of enrolled tokens will be limited to 2 (default value is 4).

<br>
<b>Prerequisites</b>

- Citrix ADC advanced edition with firmware 13.0 or newer 
- Citrix Gateway VServer where you can bind the service to
- An installed SSL certificate on this ADC

<br>
<b>Before running this Stylebook</b>

Make sure you have an LDAP service account which is able to write information in LDAP attribute "userParameters"

<b>Mandatory Settings</b>
<b>Required LDAP Parameters</b>

- LDAP Server IP - IP address of the LDAP Server
- In which BaseDN should the ADC start for searching Users? - Base DN for searching users (fe. dc=training, dc=local)
- Name of service account for authentication (UPN or DN) - Service Account which has write permissions on LDAP attribute "userParameters"
- Password for service account - I don't think this needs an explanation. 
<br>

- Access limited to following subnet - For security reasons, the self service portal is only accessible within this subnet.
<br>

- Certificate Name for VServer binding - Name of the certificate pair which is installed on Citrix ADC. This certificate will be bound to the new created AAA VServer.

<br>
<b>Manual steps after running the Stylebook</b>

Because I don't want to break any running configuration on the ADC, there are some last manual steps to do: 
- Bind the new created authentication profile to the gateway VServer
- Bind the new created traffic policy to the gateway VServer
