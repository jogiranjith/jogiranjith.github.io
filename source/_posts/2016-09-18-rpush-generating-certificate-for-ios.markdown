---
layout: post
title: "Rpush Generating certificate for ios"
date: 2016-09-07 22:59:56 +0530
comments: true
categories: ["Rpush","Ruby on Rails"]
---

To Create .pem file for apple push notification using rpush .

##Steps:
 1.Create a CSR Using Key Chain Access
 2.Create a P12 Using Key Chain Access using private key.
 3.APNS App ID and certificate.

 * This gives you three files:
   + The CSR
   + The private key as a p12 file (pushkey_production.p12)
   + The SSL certificate, aps_development.cer or the .pem file(pushkey_production.pem)

  Convert the .cer file into a .pem file:

     openssl x509 -in aps_development.cer -inform der -out pushkey_production.pem

  Convert the private key’s .p12 file into a .pem file: 

     openssl pkcs12 -nocerts -out private_keyy.p12 -in pushkey_private_production.p12
   
  Enter Import Password:     
     
     MAC verified OK
     Enter PEM pass phrase: 
     Verifying - Enter PEM pass phrase:

You first need to enter the passphrase for the .p12 file so that openssl can read it. Then you need to enter a new passphrase that will be used to encrypt the PEM file. Again for this tutorial I used “pushchat” as the PEM passphrase. You should choose something more secure. Note: if you don’t enter a PEM passphrase, openssl will not give an error message but the generated .pem file will not have the private key in it.

  Finally, combine the certificate and key into a single .pem file:

     cat pushkey_production.pem pushkey_private_production.pem >rpush_prod.pem



     

