# task -3
# Vulnerability scanning report

## Vulnerability Scanned report
** Tool Used-** Nessus Essentials
** Target-** Localhost
## Vulnerabilities Scanned

| Vulnerability rate |    Vulnerability scanned           |  Description  |
|--------------------|------------------------------------|---------------|
|     Medium         | SMB Signing not required           |Signing is not required on the remote SMB server. An unauthenticated, remote attacker can exploit this to conduct man-in-the-middle attacks against the SMB server.|
|     Medium         | SSL Certificate Cannot Be Trusted  |The server's X.509 certificate cannot be trusted.If the remote host is a public host in production, any break in the chain makes it more difficult for users to verify the authenticity and identity of the web server. This could make it easier to carry out man-in-the-middle attacks against the remote host.|
|      Low           | DCE Services Enumeration           |By sending a Lookup request to the portmapper (TCP 135 or epmapper PIPE) it was possible to enumerate the Distributed Computing Environment (DCE) services running on the remote port. |
|      Low           | Netstat Portscanner (SSH)          |Nessus was able to run 'netstat' on the remote host to enumerate the open ports. If 'netstat' is not available, the plugin will attempt to use 'ss'.|

---

## Simple fixes or mitigations
-Enforce message signing in the host's configuration. On Windows, this is found in the policy setting 'Microsoft network server: Digitally sign communications (always)'. On Samba, the setting is called 'server signing'. See the 'see also' links for further details.
-Purchase or generate a proper SSL certificate for this service.
-Using this information it is possible to connect and bind to each service by sending an RPC request to the remote port/pipe.
-This plugin will run on Windows (using netstat.exe) in the event that the target being scanned is localhost.
