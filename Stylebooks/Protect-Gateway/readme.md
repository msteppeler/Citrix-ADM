<b>About this Stylebook</b>

This Stylebook contains everything you need to protect the Citrix Gateway Login Page with WAF and BOT features. As a template I used following article in Citrix Docs: https://docs.citrix.com/en-us/tech-zone/learn/poc-guides/protect-gateway-waf-bot-aaa.html

<b>Prerequisites</b>

- Citrix ADC premium edition with firmware 13.0 or newer
- Citrix Gateway VServer with (at least) LDAP authentication activated
- Activated Features: Web App Firewall, Bot Management and Reputation

Optional Settings:
- A running Loadbalancing VServer on port 80

<b>Before running this Stylebook</b>
- Manually create a custom bot signature file. Just make a clone of the "\*Default Bot Signatures" file <br>(Security > Citrix Bot Management > Signatures)

<b>Parameters within Stylebook</b>

Required LB VServer information
- Would you like to create a new http LB VServer as a dummy for http callout or use an existing one? <br> "Existing" - if there is already a http VServer running on this ADC. <br> "NEW" - if you need to create a new http VServer on port 80
- Name of the new or existing LB VServer - Name of the http VServer the httpcallout policy will be bound to.
- IP address for a new backend server - If you choose to create a "NEW" Loadbalancing VServer, enter the ipaddress of the backend server.

- Name of the preconfigured bot signature file - The name of the signature file you've created manually before.

Required LDAP Authentication Policy settings
- Name of the new LDAP authentication policy - A new LDAP authentication will be created
- Name of the actual bound LDAP Action - The existing LDAP action will also be bound to the new LDAP authentication policy

<b>Manual steps after running the Stylebook</b>

Because I don't want to break any running configuration on the ADC, there is one last manual step to do:
On the Gateway-, or AAA-VServer unbind the actual LDAP policy and bind the new created one. That's it!
