# SSL Poke Java APP

A simple java app for an ssl poke which can be used to check a self-signed cert is working. 

Usage:

1.extract cert from serveri:
```
openssxl s_client -connect server:443
```
2.negative test cert / keytool:
```
java SSLPoke server 443
```
you should get something like
```
javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target
```
3.import cert into default keytool:
```
keytool -import -alias alias.server.com -keystore $JAVA_HOME/jre/lib/security/cacerts
```
4.positive test cert / keytool:
```
java SSLPoke server 443
```
you should get this:
```
Successfully connected
```
