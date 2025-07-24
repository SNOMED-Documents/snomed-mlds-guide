# MLDS Staff Account Setup

Currently (_2017-07-05_) MLDS uses the usermanagement server for the administrative access. Due to the shutdown of Stormpath services these need to be migrated to the Crowd user accounts and structure.

The current setup uses the following structure/permissions:

  * Member: * or specific member
  * Type: Staff or Admin or Member (used by NRCs to download SCT releases)

The equivalent structure in crowd will use groups, as there are no 'roles' as such built into Crowd. For example:

  * Admin: mlds-ihtsdo
  * Staff: mlds-staff-x (e.g. mlds-staff-be for Belgium where the group dictates which member they have access to)
  * Member: mlds-member ( users with this role will only be able to download the international edition )

These should be configurable in a config/properties file on the deployment, or alternatively, can be inserted in to the Member table in the database.

## Test Accounts

Role / Country| Username| Email| Full Name| Password| Environments| Permissions| Applications  
---|---|---|---|---|---|---|---  
Admin| use own account!|   
|   
| <use SSO IMS password >| ALL| mlds-ihtsdo|   
  
Staff - India| test-mlds-staff-india| pwi+test+mlds+india@ihtsdo.org| MLDS Test, Staff| xKgAS5XJ| DEV| mlds-staff-in| [ihtsdo-tools](https://dev-crowd.ihtsdotools.org/crowd/console/secure/application/viewdetails.action?ID=4)  
Member| test-mlds-member| pwi+test+mlds+member@[ihtsdo.org](http://ihtsdo.org)| MLDS Test, Member| ~~xKgAS5XJ~~~~Übercafé~~ ÆsirAsgård| DEV| mlds-member| [ihtsdo-tools](https://dev-crowd.ihtsdotools.org/crowd/console/secure/application/viewdetails.action?ID=4)  
Affiliate| N/A| pwi+mlds+zimbabwe@[ihtsdo.org](http://ihtsdo.org)|   
| xKgAS5XJ| DEV| N/A| N/A  
Affiliate| N/A| pwi+mlds+india2@[ihtsdo.org](http://ihtsdo.org/)| Test, India| xKgAS5XJ| DEV| N/A| N/A  
Staff - Sweden| test-mlds-staff-sweden| pwi+test+mlds+staff+sweden@[ihtsdo.org](http://ihtsdo.org)| MLDS Test, Staff Sweden| xKgAS5XJ| DEV| mlds-staff-se| [ihtsdo-tools](https://dev-crowd.ihtsdotools.org/crowd/console/secure/application/viewdetails.action?ID=4)  
  
  

## Development Issues

Issue| Resolution  
---|---  
The Stormpath code allowed us to check a proposed user account to ensure that it doesn't already exist as a staff/admin user. Is there a way with Spring SSO to check if an account name exists, without necessarily trying to log in to it?| New endpoint added to IMS to allow checking for username (and optionally, email address) without initiating the registration process. The user does not have to be logged in to use this feature
[code]
    https://dev-ims.ihtsdotools.org:443/api/pre-register-check?username=pwilliams
[/code]  
  
  
|   
  
  
|   
  
  
|   
  
  
  

  

  

