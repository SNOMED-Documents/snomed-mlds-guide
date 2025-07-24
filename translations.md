# Translations

There are three things that need translating and the necessary files can be found on this page covering the following parts:

The interface and email messages **need to be translated** , whilst the third section is optional depending on Member country preference.

## Interface

In order to add your language to the interface so that it can be chosen from the drop-down at the top of the screen, you will need to translate the following file, renaming the file from en-reduced.json to the two character representation of the relevant language (for example Danish would dk.json or French would be fr.json).

### File for translation

This file below is the version which should be translated. However, the following sections need not be translated as they are only for the administrative interface.:

\- global.menu.staff

\- global.menu.admin

\- global.sessions

\- global.tracker

\- global.metrics

\- global.logs

\- global.audits

By ignoring the above sections, the staff/admin interface will remain in English.

\[

<figure><img src="download/resources/com.atlassian.confluence.plugins.confluence-view-file-macro:view-file-macro-resources/images/placeholder-small-file.png" alt=""><figcaption><p>Please download the relevant file and once translated, send back to <a href="mailto:techsupport@ihtsdo.org">techsupport@ihtsdo.org</a> to be uploaded to the MLDS test server.</p></figcaption></figure>

en.json]\(/download/attachments/5505183/en.json?version=7\&modificationDate=1612854687000\&api=v2)

Other translation files can be found here - [https://github.com/IHTSDO/MLDS/tree/master/src/main/webapp/i18n](https://github.com/IHTSDO/MLDS/tree/master/src/main/webapp/i18n) .

If you have any questions, please don't hesitate to get in touch with [techsupport@ihtsdo.org](mailto:techsupport@ihtsdo.org) where we will help where we can.

## How to translate

If you would like to run locally on your desktop, you can use a plain text editor. In the file you will a long list of labels with the existing English translation. Each label which needs to be translated is represented with the label being on the left with the phrase to be translated on the right, i.e. \[code] label:language e.g. "help":"Aide" for French or "help":"Help" for English \[/code]

_\*\*Note that text contained within angle brackets ( < >) is for formatting and does not need to be translated. \*\*_

### Example

The following block is an example of the first part of the file containing the English version in order to demonstrate what you need to translate.

**en.json** \[code] { "global":{ "title":"mlds", "browsehappy":"You are using an **outdated** browser. Please \<a href="http://browsehappy.com/?locale=en">upgrade your browser to improve your experience.", "menu":{ "home":"Home", "account":{ "main":"Account", "contactInfo":"Contact Info", "password":"Password", "sessions":"Sessions", "tracker":"User tracker", "metrics":"Metrics", "logs":"Logs", "audits":"Audits", "login":"Login", "logout":"Log out", "apidocs":"API", "register":"Register", "affiliates":"Affiliates", "dashboard":"Dashboard" }, ... \[/code]

The next block is the same lines, but in the (machine translated) French version, \*\*note that text contained within angle brackets ( < >) is for formatting and does not need to be translated. \*\*

**fr.json** \[code] { "global":{ "title":"MLDS", "browsehappy":"Vous utilisez un navigateur **désuet**. \<a href="http://browsehappy.com/?locale=en"> Mise à niveau de votre navigateur pour améliorer votre expérience .", "menu":{ "home":"Home", "account":{ "main":"Compte", "contactInfo":"Coordonnées", "password":"Mot de passe", "sessions":"Sessions", "tracker":"Tracker Utilisateur", "metrics":"Métriques", "logs":"Logs", "audits":"Audits", "login":"Connexion", "logout":"Déconnexion", "apidocs":"API", "register":"Inscription", "affiliates":"Affiliés", "dashboard":"Table au Debord" }, ... \[/code]

## Email Messages

The following file also needs to be translated and contains the wording in the emails that get sent out.

\[

<figure><img src="download/resources/com.atlassian.confluence.plugins.confluence-view-file-macro:view-file-macro-resources/images/placeholder-small-file.png" alt=""><figcaption><p>Please download the file and once translated, send back to <a href="mailto:techsupport@ihtsdo.org">techsupport@ihtsdo.org</a> to be uploaded to the MLDS test server.</p></figcaption></figure>

messages\_en.properties]\(/download/attachments/5505183/messages\_en.properties?version=4\&modificationDate=1612854724000\&api=v2)

Other existing email message translation files can be found here - [https://github.com/IHTSDO/MLDS/tree/master/src/main/resources/mails/messages](https://github.com/IHTSDO/MLDS/tree/master/src/main/resources/mails/messages)

The file format is slightly different and is as follows: \[code] label=language e.g. activation.greeting=Cher {0} (for French) or activation.greeting=Dear {0} (for English) \[/code]

## Other Files

The following files may also need to be translated to be added to the site, mainly around terms & conditions and the affiliate license. This is a more straightforward translating of the contents of the files but the choice to translate these files is up to the Member country.

Terms of Service -



Affiliate License -

