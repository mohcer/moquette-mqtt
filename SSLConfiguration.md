# Introduction #

Here are some simple steps to do to configure Moquette to serve over SSL

# Details #
Moquette uses JavaKeyStore and certificates to handle SSL. In order to expose it over SSL you have create a keystore for the broker (select the password), exporting a certificate and define 4 variables into moquette.conf.

## Create a keystore ##
In a directory generate the keystore using the JRE's keytool:
```
keytool -keystore serverkeystore.jks -alias testserver -genkey -keyalg RSA
```
To make it work you have to answer at the first question, say `moquette.dna.org` and as password we could use passw0rdsrv for both (keystore and keymanger)

## Export a certificate ##
Then you need export a certificate:
```
 keytool -export -alias testserver -keystore serverkeystore.jks -file testserver.crt
```

## Imporing on the client side ##
Supposing you have already created the keystore for the client side, (name it clientkeystore for example), we could import the certificate with:
```
keytool -keystore clientkeystore.jks -import -alias testserver -file testserver.crt -trustcacerts
```

It's done! We just need use the Paho client to connect to the server, check ServerIntegrationSSLTest.java integration test to see how.