# Introduction #
These are the steps I use to export and bundle a versioned-tarball for the downloads page.

# Details #
```
svn export https://java-exportpriv.googlecode.com/svn/trunk/ java-exportpriv
mv java-exportpriv java-exportpriv-1.0
tar czvf java-exportpriv-1.0.tgz java-exportpriv-1.0/
```

Now the .tgz file can be uploaded.