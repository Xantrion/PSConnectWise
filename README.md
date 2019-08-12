**Looking for Someone to Take Ownership of this Project**

# PSConnectWise  

Collection of PowerShell functions that interface with ConnectWise's REST API service. This project
is meant to target the latest general releases of PowerShell (i.e. PS v5.0) and ConnectWise.

### Functions
Goal of the version of v1.0 was to create the minimum required PowerShell functions that is needed 
to properly create, read, update, and delete a ConnectWise ticket. While doing so, develop a core 
that will easly allow for future functions to be added. 

###### Service Module
0. `Get-CWServiceTicket`
0. `New-CWServiceTicket`
0. `Update-CWServiceTicket`
0. `Remove-CWServiceTicket`
0. `Get-CWServiceBoard`
0. `Get-CWServiceBoardStatus`
0. `Get-CWServiceBoardType`
0. `Get-CWServiceBoardSubtype`
0. `Get-CWServicePriority`
0. `Get-CWServiceTicketNote`
0. `Add-CWServiceTicketNote`

###### Company Module
0. `Get-CWCompany`
0. `Get-CWCompanyContact`

###### TimeEntry Module
0. `Get-CWTimeEntry`
0. `Add-CWTimeEntry`
0. `Update-CWTimeEntry`
0. `Remove-CWTimeEntry`

###### System Module
0. `Get-CWSystemMember`
0. `Set-CWSession`
0. `Test-CWSession`
        
## Requirements

- PowerShell 5.0
- ConnectWise Server v2015.3 or Newer
- [CW Member's Public and Private API Key](./doc/DevCreateCWApiKey.md)
- FQDN to the ConnectWise (API) Server
  - On permise CW server and CW API server are the same.
  - Cloud based CW server and CW API server are **not** the same.

## Import Module to PS Session

0. Download or Clone this Repository
0. Open PowerShell
0. Import the Module (.psm1) within the `PSConnectWise` Directory
   - `Import-Module "...\PSConnectWise\PSConnectWise\PSConnectWise.psm1" -Force;`
0. Functions are Imported and Ready to Use

## Examples

#### Get ConnectWise Ticket

##### Execute
```powershell
$CWSession = Set-CWSession -Domain 'TechInUrPocket.example.com' -CompanyName 'TechInUrPocket' -PublicKey '...' -PrivateKey '...';`
Get-CWServiceTicket -ID 1234567 -Session $CWSession;  # Session parameter and value not required
```
##### Returns
```powershell
id                         : 1234567
summary                    : My Computer is Broken
recordType                 : ServiceTicket
board                      : @{id=1; name=BreakFix; _info=}
status                     : @{id=1; name=New; _info=}
... 
```

## Contributing

See the [Contributing Documentation](./CONTRIBUTING.md)

## Extra Information
- This module (v1.0) is still under development. 
  - This means breaking changes can be introduced by future updates.
  - Once the v1.0 module has be [published](https://github.com/sgtoj/PSConnectWise/milestone/1) to the [PowerShell Gallery](https://www.powershellgallery.com/), versions and breaking changes will follow [semantic versioning](http://semver.org/) convention. 
- [Test Directory](./test/) Stores the Unit Test Scripts for [Pester](https://github.com/pester/Pester).
  - See [Readme](https://github.com/sgtoj/ConnectWisePSModule/tree/master/pester)
- [Documented Architecture](https://github.com/sgtoj/ConnectWisePSModule/blob/master/doc/ClassArchitectures.md) of the Dependent PS Classes
  - It is not required to read or understand it to use PowerShell function.
  - Its target is future contributors to this project.
  
## License

[MIT](./LICENSE.txt)
