<b>About this Stylebook</b>

Logging on to Citrix ADC with local user accounts isn't really best practise. 
So with this stylebook you activate external authentication with LDAP as first factor and OTP as a second factor.
I assume there is a OTP policy configured.


<b>Prerequisites</b>
- Citrix ADC 12.1 or newer
- Already configured OTP System in the backend


<b>Mandatory Settings Required LDAP Parameters</b>

- LDAP Server IP - IP address of the LDAP Server
- In which BaseDN should the ADC start for searching Users? - Base DN for searching users (fe. dc=training, dc=local)
- Name of service account for authentication (UPN or DN) - Service Account which has write permissions on LDAP attribute "userParameters"
- Password for service account - I don't think this needs an explanation.
- Name of the LDAP group which is allowed to access Citrix ADC - Members of this group get superuser permissions on Citrix ADC
- DN of the group - complete DN to build the searchfilter.

<b>Required OTP information</b>

- Name of the OTP Policy - This policy is used as a second factor.

<b>Note:</b>
Local useraccounts are not disabled and still work. You need local user accounts for ADM access. Local user accounts which are not required anymore should be deleted!
