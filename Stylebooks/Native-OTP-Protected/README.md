<b>About this Stylebook</b>

There are situations where it is necessary to make the manageotp site public available. To protect this via LDAP Login only does not provide adequate security.
So this Stylebook creates a Native OTP solution and protects the manageotp site with a second factor. This factor is email-OTP. 
This one time password is send to the customers company mail address.


<b>Prerequisites</b>
- Citrix ADC advanced edition with firmware 13.0 or newer
- Citrix Gateway VServer where you can bind the service to
- An installed SSL certificate on this ADC


<b>Before running this Stylebook</b>
Make sure you have an LDAP service account which is able to write information in LDAP attribute "userParameters"

<b>Mandatory Settings Required LDAP Parameters</b>

- LDAP Server IP - IP address of the LDAP Server
- In which BaseDN should the ADC start for searching Users? - Base DN for searching users (fe. dc=training, dc=local)
- Name of service account for authentication (UPN or DN) - Service Account which has write permissions on LDAP attribute "userParameters"
- Password for service account - I don't think this needs an explanation.

<b>Mandatory Settings Required mail settings</b>
- Mailaddress of service account which sends eOTP mail - This service account will authenticate against the SMTP server and needs permissions to send mails via SMTP.
- Password - Password of the service account which sends the email
- IP-address or FQDN of mail server - You can enter either ip-address or FQDN of the mailserver which sends the mail.
- Which Protocol to use (SMTP/SMTPS) - Choose the protocol the mail server accepts. 
- Which Port to use (25/587/465) - Choose the port the mail server listens to.

Certificate Name for VServer binding - Name of the certificate pair which is installed on Citrix ADC. This certificate will be bound to the new created AAA VServer.

<b>Manual steps after running the Stylebook</b>
Because I don't want to break any running configuration on the ADC, there are some last manual steps to do:

- Bind the new created authentication profile to the gateway VServer
- Bind the new created traffic policy to the gateway VServer
