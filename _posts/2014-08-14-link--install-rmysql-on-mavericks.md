---
layout: post
title: "Install RMySQL on Mavericks"
description: ""
category: Mac
tags: [R]
comments: true
share: true
link: http://andorian.blogspot.co.uk/2013/10/rmysql-on-osx.html
---

- MySQL: <http://dev.mysql.com/downloads/mysql/>
- R: <http://cran.r-project.org/mirrors.html>
- RStudio: <http://www.rstudio.com/products/rstudio/download/>

{% highlight mysql %}
install.packages("RMySQL")
# package ‘RMySQL’ is available as a source package but not as a binary
> install.packages('RMySQL', type='source')
/*
...
Configuration error:
  could not find the MySQL installation include and/or library
  directories.  Manually specify the location of the MySQL
  libraries and the header files and re-run R CMD INSTALL.

INSTRUCTIONS:

1. Define and export the 2 shell variables PKG_CPPFLAGS and
   PKG_LIBS to include the directory for header files (*.h)
   and libraries, for example (using Bourne shell syntax):

      export PKG_CPPFLAGS="-I<MySQL-include-dir>"
      export PKG_LIBS="-L<MySQL-lib-dir> -lmysqlclient"

   Re-run the R INSTALL command:

      R CMD INSTALL RMySQL_<version>.tar.gz
...
*/
Sys.setenv(PKG_CPPFLAGS = "-I/usr/local/mysql-5.6.20-osx10.8-x86_64/include/")
Sys.setenv(PKG_LIBS = "-L/usr/local/mysql-5.6.20-osx10.8-x86_64/lib -lmysqlclient")
install.packages("RMySQL", type = "source")
/*
...
Error : .onLoad failed in loadNamespace() for 'RMySQL', details:
  call: dyn.load(file, DLLpath = DLLpath, ...)
  error: unable to load shared object '/Library/Frameworks/R.framework/Versions/3.1/Resources/library/RMySQL/libs/RMySQL.so':
  dlopen(/Library/Frameworks/R.framework/Versions/3.1/Resources/library/RMySQL/libs/RMySQL.so, 6): Library not loaded: libmysqlclient.18.dylib
...
*/
{% endhighlight %}

Now in iTerm 2,
{% highlight bash %}
echo "R.home()" | Rscript  /dev/stdin
# [1] "/Library/Frameworks/R.framework/Resources"
fgrep MYSQL_HOME /Library/Frameworks/R.framework/Versions/3.1/Resources/etc/Renviron
# nothing return
echo 'MYSQL_HOME="/usr/local/mysql-5.6.20-osx10.8-x86_64"' >> /Library/Frameworks/R.framework/Versions/3.1/Resources/etc/Renviron
ln -s /usr/local/mysql-5.6.20-osx10.8-x86_64/lib/libmysqlclient.18.dylib /Library/Frameworks/R.framework/Resources/lib
{% endhighlight %}

Next in RStudio,

{% highlight mysql %}
> install.packages("RMySQL", type = "source")
# ...
# * DONE (RMySQL)
# ...
{% endhighlight %}

