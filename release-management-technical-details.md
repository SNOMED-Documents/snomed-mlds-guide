# Release Management Technical Details

MLDS contains a number of releases from different sources, this is a combination of Snomed International releases, Managed Service releases and also National Release Center (NRC) release. 

## Snomed International Releases

The release process will populate the **snomed-releases** S3 bucket automatically and when adding a new release onto MLDS these archives should be linked to in MLDS, e.g.

<https://snomed-releases.s3.amazonaws.com/prod/published/international/SnomedCT_InternationalRF2_PRODUCTION_20221231T120000Z.zip>

  

Additional release files are created and should be linked in the same way, e.g.

<https://snomed-releases.s3.amazonaws.com/prod/published/international/SnomedCT_GeneralDentistry_PRODUCTION_20221130T120000Z.zip>

**Note** that there are still some older releases using an older S3 bucket, **release-ihtsdo-prod-published** e.g..

<https://release-ihtsdo-prod-published.s3.amazonaws.com/se/SnomedCT_ManagedServiceSE_PRODUCTION_SE1000052_20171130T120000Z.zip>

## Managed Service Releases

Same as International but folder prefix will contain the Country code, e.g.

<https://snomed-releases.s3.amazonaws.com/prod/published/nz/SnomedCT_ManagedServiceNZ_PRODUCTION_NZ1000210_20221001T000000Z.zip>

Any additional release files not created via the Managed Service would need to be uploaded and linked via the next section

**Note** that there are still some older releases using an older S3 bucket, **release-ihtsdo-prod-published** e.g..

<https://release-ihtsdo-prod-published.s3.amazonaws.com/se/SnomedCT_ManagedServiceSE_PRODUCTION_SE1000052_20171130T120000Z.zip>

## NRC or Additional releases from MS customers

There are a number of additional S3 buckets used for these;

ihtsdo-mlds.be  
ihtsdo-mlds.fi  
ihtsdo-mlds.in  
ihtsdo-mlds.int  
ihtsdo-mlds.nl  
ihtsdo-mlds.nz  
ihtsdo-mlds.se  

e.g.

<https://ihtsdo-mlds.be.s3.amazonaws.com/xdoc_3BT-SnomedCTMapPackage-ReleaseNotes_Current-en-20220315.pdf>

## Old notes, not sure if needed or not.

The IHTSDO release team will package the SNOMED CT International Release as normal. The IHTSOD technical group will upload the files to MLDS.

Admin users enter a URL in one of 3 forms:

  1. A normal URL from any openly accessible location
  2. A normal URL from a secure S3 location e.g. <https://ire.published.release.ihtsdo.s3.amazonaws.com/international/SnomedCT_Release_INT_20140131.zip>
  3. An S3 protocol locator e.g. s3://ire.published.release.ihtsdo/international/SnomedCT_Release_INT_20140131.zip

If member countries also want to enter an S3 location, there is no way to enter secure credentials into the system on a per location basis at this stage. For member files they should go into the following S3 buckets:

ire.published.release.ihtsdo/extensions/<country code>, e.g. ire.published.release.ihtsdo/extensions/DK/file.zip

### Specific S3 Member Buckets

Some members have their own S3 bucket for files which are not SNOMED CT releases:

**Belgium** \- <https://ihtsdo-mlds.be.s3.amazonaws.com/> name>

**Finland** \- <https://ihtsdo-mlds.fi.s3.amazonaws.com/> name>

**New Zealand** \- https://ihtsdo-mlds.nz.s3.amazonaws.com/<file name>

**Netherlands** \- https://ihtsdo-mlds.nl.s3.amazonaws.com/<file name>

**Sweden** \- <https://ihtsdo-mlds.se.s3.amazonaws.com/> name>

**NOTE: The url above is NOT the normal S3 file link ( e.g.https://s3.amazonaws.com/ihtsdo-mlds.nl/<file name>) _You need to use the links above._**

**Ensure you test the file can be downloaded after adding it to make sure it is accessible.**

**Testing the URL directly will show Access Denied - You need to add to MLDS and then test the download from the UI**
