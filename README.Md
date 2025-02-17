$searchBase = "CN=Active Directory Web Services,CN=Services,CN=Configuration,DC=yourdomain,DC=com"

Get-ADObject -SearchBase $searchBase -LDAPFilter "(objectClass=serviceConnectionPoint)" -Properties keywords, serviceBindingInformation | 
    Where-Object { $_.keywords -like "*adws*" } | 
    Select-Object Name, serviceBindingInformation
