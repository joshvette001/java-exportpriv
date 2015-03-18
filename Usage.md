# Introduction #

This page explains how to compile and use exportpriv

It assumes you've already downloaded the code, either from the Downloads section (http://code.google.com/p/java-exportpriv/downloads/list) or using your svn client.

For more information about the procedure, alternatives and possible outcomes, see http://conshell.net/wiki/index.php/Keytool_to_OpenSSL_Conversion_tips

# Details #
## Compile ##
Change into the folder containing the source code files.
```
cd java-exportpriv/
```
You must compile using javac. This creates the .class files used by Java.
```
javac ExportPriv.java Base64Coder.java
```

## Usage ##
```
java ExportPriv <keystore> <alias> <password>
```

Example
```
$ java ExportPriv .keystore mykey test123

-----BEGIN PRIVATE KEY-----
MIIBSwIBADCCASwGByqGSM44BAEwggEfAoGBAP1/U4EddRIpUt9KnC7s5Of2EbdS
PO9EAMMeP4C2USZpRV1AIlH7WT2NWPq/xfW6MPbLm1Vs14E7gB00b/JmYLdrmVCl
pJ+f6AR7ECLCT7up1/63xhv4O1fnxqimFQ8E+4P208UewwI1VBNaFpEy9nXzrith
1yrv8iIDGZ3RSAHHAhUAl2BQjxUjC8yykrmCouuEC/BYHPUCgYEA9+GghdabPd7L
vKtcNrhXuXmUr7v6OuqC+VdMCz0HgmdRWVeOutRZT+ZxBxCBgLRJFnEj6EwoFhO3
zwkyjMim4TwWeotUfI0o4KOuHiuzpnWRbqN/C/ohNWLx+2J6ASQ7zKTxvqhRkImo
g9/hWuWfBpKLZl6Ae1UlZAFMO/7PSSoEFgIUSqXovCQu+athtYMTdD71QvJFn/M=
-----END PRIVATE KEY-----
```

The private key is printed to stdout as PKCS#8 PEM format. To get it right into the DSA format that works with Apache (see below) you can convert it openssl command:

```
java ExportPriv .keystore mykey test123 | openssl pkcs8 -inform PEM -nocrypt

-----BEGIN DSA PRIVATE KEY-----
MIIBuwIBAAKBgQD9f1OBHXUSKVLfSpwu7OTn9hG3UjzvRADDHj+AtlEmaUVdQCJR
+1k9jVj6v8X1ujD2y5tVbNeBO4AdNG/yZmC3a5lQpaSfn+gEexAiwk+7qdf+t8Yb
+DtX58aophUPBPuD9tPFHsMCNVQTWhaRMvZ1864rYdcq7/IiAxmd0UgBxwIVAJdg
UI8VIwvMspK5gqLrhAvwWBz1AoGBAPfhoIXWmz3ey7yrXDa4V7l5lK+7+jrqgvlX
TAs9B4JnUVlXjrrUWU/mcQcQgYC0SRZxI+hMKBYTt88JMozIpuE8FnqLVHyNKOCj
rh4rs6Z1kW6jfwv6ITVi8ftiegEkO8yk8b6oUZCJqIPf4VrlnwaSi2ZegHtVJWQB
TDv+z0kqAoGABE1QRo8k8otzUpmIN3QL9aDjHBdPExBJ1eHQDzsrKAGqBoOum9Ub
0krYz691XVhVAJ60F7dZonU11IzAqsWwG8mcnef1CCDi/r8iEcidljsuUdS3aV26
dhePkkqnHQmDwtfGwFur2ijxTh4i0MCLI9dTmsY3nMXAeJACVpass8kCFEql6Lwk
LvmrYbWDE3Q+9ULyRZ/z
-----END DSA PRIVATE KEY-----

```