1. Create a keystore
```
$ keytool -genkeypair -alias test -keystore .keystore
Enter keystore password:  
Re-enter new password: 
What is your first and last name?
  [Unknown]:  mark
What is the name of your organizational unit?
  [Unknown]:  none
What is the name of your organization?
  [Unknown]:  none
What is the name of your City or Locality?
  [Unknown]:  none
What is the name of your State or Province?
  [Unknown]:  none
What is the two-letter country code for this unit?
  [Unknown]:  no 
Is CN=mark, OU=none, O=none, L=none, ST=none, C=no correct?
  [no]:  y

Enter key password for <test>
	(RETURN if same as keystore password):  
```

2. Compile the .java files
```
$ cd /tmp/java-exportpriv-1.0/
$ javac ExportPriv.java Base64Coder.java
```

3. Extract the test alias from the keystore
```

$ java ExportPriv /home/mdf/.keystore test testpw
-----BEGIN PRIVATE KEY-----
MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdS
PO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVCl
pJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith
1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7L
vKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3
zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImo
g9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUEmCYFSQIRytEiwiKjYOrwQUWxZg=
-----END PRIVATE KEY-----
```