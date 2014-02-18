Verndale Misc Multilingual Updates for Sitecore

Purpose
Move embedLanguage to a site specific setting, add custom LinkManager, set .net culture based on sitecore context language for formatting dates, currencies, etc.

Compatibility
The codebase is compatible with Sitecore 6.6.x releases and should be compatible with earlier releases.
This assumes you are using the latest version of the Partial Language Fallback Module
http://marketplace.sitecore.net/en/Modules/Language_Fallback.aspx
However you shouldn't have to use fallback for these updates, you could just grab the updates out of the config file an apply them within a different config

How to build code and deploy the solution
1. When using the fallback module, make sure to compile the source code to get the dll, do not use the one within the package.

2. Download and unzip the Verndale.SharedSource.zip from this repository, it contains a class library
3. The important file in this are CustomLinkProvider.cs, CultureResolver.cs

4. Download the App_Config folder, there are necessary updates within Sitecore.SharedSource.PartialLanguageFallback.config.example
You can use the whole thing or take the parts from it that you need and add to your own config
It contains an additional class to be used in the httpRequestBegin pipeline, which checks the CultureResolver class, 
this will update the .NET culture based on the Sitecore context language
It also contains a custom LinkManager Provider which will check for a site specific setting for languageEmbedding

Testing
1. Set the languageEmbedding for the LinkManager to 'never', but then within your site node, set it to 'always'
2. See that links are output with the language embedded in it
3. Output some dates and currencies, view in an English language and then in another language
4. See that the formatting actually outputd different currency signs and date formats, etc

Review the blog series about Partial Language Fallback on Sitecore, link TBD
