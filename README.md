# ankidroid-http-conection
simple tutorial in how to use http connection in ankidroid to use the anki-sync-server

from the version 2.10 to the newest, ankidroid only allow https connections to private server for security reasons. That makes it harder to use this feature, because simple homeservers that are only going to be deployed in local network would need the use of SSL certificates.

to allow http connections is just necessary to change the file **AnkiDroid/src/main/res/xml** in the source code to include the ip of the server
example: 
```
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
    <base-config>
        <trust-anchors>
            <!-- Trust preinstalled CAs -->
            <certificates src="system" />
            <!-- Additionally trust user added CAs -->
            <certificates src="user" />
        </trust-anchors>
    </base-config>
    <domain-config cleartextTrafficPermitted="true">
        <domain includeSubdomains="true">localhost</domain>
        <domain includeSubdomains="true">127.0.0.1</domain>
        <domain includeSubdomains="true">192.168.194.1</domain>
    </domain-config>
</network-security-config>
`

after this you just need to compile and run the application on your utilizing the ip to the custom server
  
