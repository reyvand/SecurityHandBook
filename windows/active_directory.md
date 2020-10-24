# **Active Directory 101

[Active Directory](https://searchwindowsserver.techtarget.com/definition/Active-Directory#:~:text=Active%20Directory%20(AD)%20is%20Microsoft's,device%2C%20e.g.%2C%20a%20printer.)

AD (_Active Directory_) merupakan _directory service_ yang ada pada sistem operasi windows. AD menyimpan informasi di dalam network sehingga dapat diakses oleh _users_ atau admin yang memiliki hak akses.

# **Active Directory - Components

* Schema - Mendefinisakn _objects_ dan _attributes_ data.
* Query dan indexing - Digunakan untuk melakukan pencarian terhadap _objects_ dan _attributes_.
* Global catalog - Menyimpan seluruh informasi tentang _objects_ yang tersimpan di direktori.
* Replication Service - Mendistribusikan data ke beberapa domain yang berbeda.

# **Active Directory - Strutures

* Forest, _domain_ dan _organization units_ (OUs) adalah dasar dari sebuah active directory 

![AD Structure in Nutshell](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/media/forest-design-models/b1ddb47e-78a5-49c7-bb21-d7421b7b84b8.gif)

_Forest_ adalah sebuah rule yang membungkus beberapa domain. 

_Domain_ adalah network area yang dikontrol oleh satu authentication database.

_Oraganization Units_ adalah satu wadah untuk menyimpan data2 yang disimpan di AD.

# **Cheatset 

# Domain Enumeration (PowerShell)

Disini kita bisa menggunakan 2 tools untuk melakukan enumerasi : 
* PowerView (https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1)
* Module Active Directory dari Microsoft (https://docs.microsoft.com/en-us/powershell/module/addsadministration/?view=win10-ps) 

• Getthecurrentdomain(PowerView): 
```ps1
    Get-NetDomain
    Get-NetDomain -Domain powershell.local
    GetthecurrentdomainSID Get-DomainSID
# Active Directory module:
    Get-ADDomain
    Get-ADDomain -Identity powershell.local (Get-ADDomain).DomainSID.Value
```


• Get domain controllers for a domain: 
```ps1
    Get-NetDomainController
    Get-NetDomainController -Domain powershell.local
# Active Directory module:
    Get-ADDomainController
    Get-ADDomainController -Discover -DomainName powershell.local
```

• Get users of a domain
```ps1
    Get-NetUser
    Get-NetUser -Domain powershell.local 
    Get-NetUser –UserName labuser
# Active Directory module
    Get-ADUser -Filter * -Properties * 
    Get-ADUser -Server ps-dc.powershell.local 
    Get-ADUser -Identity labuser
```

• Get all the groups in the current domain Get-NetGroup
```ps1
    Get-NetGroup *admin*
# Using Active Directory Module
    Get-ADGroup -Filter * | select Name
    Get-ADGroup -Filter 'Name -like "*admin*"' | select Name
```

• Get all computers of the domain 
```ps1
    Get-NetComputer Get-NetComputer -FullData
# Using Active Diretory module
    Get-ADComputer -Filter * | select Name Get-ADComputer -Filter * -Properties *
```

• Find all machines on the current domain where the current user has local admin access
```ps1
    Find-LocalAdminAccess -Verbose
```

• Find local admins on all machines of the domain. 
```ps1
    Invoke-EnumerateLocalAdmin -Verbose
```

• ListSessionsonaparticularcomputer 
```ps1
    Get-NetSession -ComputerName ops-dc
```

• Find computers where a domain admin is logged in and current user has access.
```ps1
    Invoke-UserHunter –CheckAccess
```






