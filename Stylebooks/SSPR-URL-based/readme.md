<b>About this Stylebook</b>

Resetting user passwords is one of the most often and most boring tasks for helpdesk. This stylebook helps configuring SelfService Password Reset (SSPR) on Citrix ADC. Users can register to this service and change forgotten passwords by their own. To register they need to have access to their company mail, because register site is protected with email-OTP.

<b>Prerequisites</b>

- Citrix ADC advanced edition with firmware 13.0 or newer
- Citrix Gateway VServer 

<b>Before running this Stylebook</b>
- The ADC admin needs to configure the KBA-Loginschema and define the questions. Also alternate email checkbox needs to be activated.
- Make sure you have an LDAP service account which is able to write information in your choosen LDAP attribute. Default: "userParameters"

<b>Parameters within Stylebook</b>

<b>Mandatory Settings Required LDAP Parameters</b>

- LDAP Server IP - IP address of the LDAP Server
- In which BaseDN should the ADC start for searching Users? - Base DN for searching users (fe. dc=training, dc=local)
- Name of service account for authentication (UPN or DN) - Service Account which has write permissions on LDAP attributes
- Password for service account - I don't think this needs an explanation.
- In which LDAP attribute shall the SSPR information be stored? - Default LDAP attribute userParameters. Maybe you want to choose a different one.

<b>Mandatory Settings Required mail settings</b>

- Mailaddress of service account which sends eOTP mail - This service account will authenticate against the SMTP server and needs permissions to send mails via SMTP.
- Password - Password of the service account which sends the email
- IP-address or FQDN of mail server - You can enter either ip-address or FQDN of the mailserver which sends the mail.
- Which Protocol to use (SMTP/SMTPS) - Choose the protocol the mail server accepts. 
- Which Port to use (25/587/465) - Choose the port the mail server listens to.
<br>
<br>
- Name of the pre-defined KBA registration schema - This is the Loginschema you have defined in Prerequisites segment above<br>
- Certificate Name for VServer binding - This certificate pair will be bound to the new authentication vserver and will be used as userdataencryptionkey.<br> 
<br>
<b>Manual steps after running the Stylebook</b>

Because I don't want to break any running configuration on the ADC, there is one last manual step to do:
On the Gateway-VServer unbind the actual login-profile and bind the new created one (Auth_Prof_SSPR). That's it!
