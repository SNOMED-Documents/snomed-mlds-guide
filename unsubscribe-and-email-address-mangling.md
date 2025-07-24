# Unsubscribe and email address mangling

# Unsubscribing

MLDS-962 added a new column to the user table "accept_notficiations" which is true by default. Setting this field to false for a user will prevent them from receiving automatic emails when a new package version is made available online.

There is no functionality in place for preventing other workflow related emails like Application Approval, Application Pending or manual Announcements, which may have financial or clinical safety implications.

To prevent a user from receiving these automatic notifications perform the following:

  

[code] 
    ssh mlds.ihtsdotools.org
    
    sudo -u mlds psql
    
    update t_user set accept_notifications = false where email = 'user.email@here';
    
    \q
    
    exit
[/code]

  

In addition, [Andrew Atkinson](https://confluence.ihtsdotools.org/display/~aatkinson) should be informed as he maintains his own user distribution list in order to send out more detailed notifications.

I would suggest that a spreadsheet is kept of all opt outs incase we ever mess up this setting and need to reset the flag globally.

Note that users are held in two separate locations. NRC / staff logins are held in IMS and there is no flag there for preventing emails from being sent. Only affiliate users (which are held in the MLDS Postgres database in the t_user table) can be modified in this way.

  

# Email Address Mangling

When production data is restored into Dev or UAT, we would normally ensure that the email server settings in /etc/opt/mlds/config.properties are set to invalid values to ensure that real-world users do not receive emails generated during Dev/UAT testing.

However, where testing is required on the email functionality itself, the email addresses can be switched so that they all go to one user, but with the original address still sort of intact. For example: pwi+mlds+[paula.diazr_redsalud.gov.cl](http://paula.diazr_redsalud.gov.cl)@[snomed.org](http://snomed.org)

To do this, run the following steps:

  

[code] 
    ssh dev-mlds.ihtsdotools.org
    
    sudo -u mlds psql
    
    update t_user set email = concat('pwi+mlds+',translate(email,'@','__'),'@snomed.org')
    
    \q
    
    exit
[/code]

  

