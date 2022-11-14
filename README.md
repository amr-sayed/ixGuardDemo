# ixGuardDemo

## Table of contents
* Create ixGuard account
* Install ixGuard Package
* Start IPA obfustication
* Upload the obfusticated IPA 
* Troubleshoting


## Create ixGuard account
First you need to create account on ixGuard to be able to download ixGuard package
and to have access on the docs

## Install ixGuard Package
After installing the .pkg file it will open a terminal,
with ixguard-docs command, this will open the documentation to you, also you can run this command anytime if you want 
to see the documentation 


## Start IPA obfustication
After generating the IPA from xcode you will have two important files

* ig-config.yml
* ixguard-license.txt


### ig-config.yml

This is the configuration file that have what ixGuard to do in the protected IPA
it have 3 important parameters 

* identity.  is the hash for the certificate you want to sign with (Development or production) 
  you can get the identity hash key from this command (xcrun security find-identity -v -p codesigning)
* provisioning. is the path of the provesioning profile that you want to sign with (Development or production)
* license. is the path of the license you got from ixGuard

## ixguard-license.txt
is the path of the license you got from ixGuard it contains your app bundle identifier, version of the ixGuard and the license key


after you get these two files put the ig-config.yml in the generated IPA folder and make sure you set the correct paths for provisioning, license 
and the right identity on this file 

# Time for the obfustication 

after setting the ixguard-license.txt inside the generated IPA folder run this command ixguard -config=ig-config.yml -o=protectedIPA.ipa yourIPA.ipa,
it will take a while to generate the protectedIPA file 


# Upload the obfusticated IPA 
It is preferd to sign the IPA with appStore certificate when you generating from xcode and then in ig-config.yml file sign it with development.
I mean you can set the identity and provisioning with development and test your IPA 
and thesn resign it with appStore certificate hash and provisioning after that you can use transporter to upload to app store  

# Troubleshoting
Before using the ixGuard make sure from the below 

1- Make sure you have the lates versions of your pods libraries 
2- Make sure you set the right paths and identity inside ig-config.yml
3- Make well testing for the obfusticated IPA before launching as sometimes it leads to crashes
















