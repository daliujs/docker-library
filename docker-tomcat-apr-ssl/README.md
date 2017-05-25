Apache Tomcat with APR native libraries and SSL support
========================================================

Apache Tomcat built with APR native libraries and SSL support


### How to build
```
docker build -t doeasy/tomcat-apr-ssl .
```

### How to run
```
docker run -d -p 80:80 -p 443:443 \
	-v <path2your-certs>:/usr/local/tomcat/conf/certs \
	-v <path2local-webapps>:/usr/local/tomcat/webapps \
	--name tomcatssl \
	doeasy/tomcat-apr-ssl
```

### SSL support

You must create a private key and a certificate for your server then copy thos files to tomcat conf folder.
Take a look at server.xml ;-)



