![Logo](https://uploads-ssl.webflow.com/6075edc3d43acf0612ddd29d/607605ecf795d582bebf9842_eVerge-logo-ko.svg)

# RapidDoc®

RapidDoc® is a powerful PDF document generator built 100% natively on the Salesforce Platform, making it easy and seemless to generate highly customized documents. Made easy for everyone, not just Admins and Developers!

## Features

- Native User Friendly Drag and Drop Document Builder
- E-Sign
- 20 Pre-Built Components
- Ability to Embed Visualforce Pages into Documents
- Ability to Embed custom Lightning Web Components into Documents
- Real Time and Reportable Document Metrics

## Installation

[![Install Managed Package in a Sandbox](./images/btn-install-managed-package-sandbox.png)](	https://test.salesforce.com/packaging/installPackage.apexp?p0=04tHp000001dSPV)
[![Install Managed Package in Production](./images/btn-install-managed-package-production.png)](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tHp000001dSPV)

`sf package install --wait 30 --security-type AdminsOnly --package 04tHp000001dSPV`

`sfdx force:package:install --wait 30 --securitytype AdminsOnly --package 04tHp000001dSPV`

## Documentation

[Documentation](https://linktodocumentation)

## FAQ
#### Why Cant I generate on mobile?
#### Can I Use RapidDoc for document generation and my E-Sign provider for E-Signing?

## Troubleshooting
#### My PDF's are taking a long time to load, why is that?

- The more components that are embeded into the Document the longer it will take to load, so keep that in mind while building documents
- Having Debug Mode on greatly slows down performance

#### Why can I not see any custom Components in the List of Components?

- If you have never setup the Authentication Metadata, or recently have refreshed the sandbox RapidDoc® is installed in you will need to reset the authentication metadata. RapidDoc® reads the list of available Components Via the Salesforce Tooling API, which requires a REST based call to utilize. We use a Connected App and Named Credentials to securely call into your Salesforce org using OAuth 2.0 Protocols.
- If the Metadata is present please ensure the following criteria is met
  - The Connect App Client Id and Secret are Match the Client Id and Secret in the RapidDoc® _Auth Providers_
  - The Named Credential _RapidDoc_ has the Enabled For Callouts Toggle set to **True**
  - The Permission Set _RapidDoc NamedCredential Access_ is assigned the External Credential Principal
  - The Permission Set _RapidDoc NamedCredential Access_ is assigned to the user experiencing the issue

#### Why can I not see a custom component in the List of Components, but can see others?

- Ensure the Component Exists in the Environment and that your Named Credential is pointing to the Correct Environment
- Ensure the LWC isExposed XML Element is Set to **True**
  - _This is because salesforce restricts code from being access across name spaces for private components. Marking it as exposed allows the RapidDoc Builder to utilize the component_

#### Why am I getting an error _Access Check Failed! AuraComponentService.createComponentFromConfig():_ when adding my custom component?

- This can happen if a component that was previously exposed has had the isExposed attribute set to false after the component was added to your document
- Another potential issue is that your Org has not enable Lightning Web Security (LWS). This new Security solution from Salesforce allows cross namespace component initialization. For more information on LWS please visit this [Salesforce Documentation Page](https://developer.salesforce.com/docs/platform/lwc/guide/security-lwsec-intro.html)

#### Why can't I specify Parameters to my custom component?

- In order to add parameters to a custom component you must expose them as Target Config Properties in the LWC XML File. For more Information please Visit this [Salesforce Documentation Page](https://developer.salesforce.com/docs/platform/lwc/guide/reference-configuration-tags.html)
  - _Please note that data sources from custom apex data sources are not currently supported_

## Screenshots

**_COMING SOON_**

## Authors

- [Tyler Brooks](https://www.linkedin.com/in/tyler-brooks-663720159)

## Support

For support, please visit our [Website](https://www.evergegroup.com/contact-us).
