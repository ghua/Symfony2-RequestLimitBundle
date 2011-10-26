README
========


Overview
---------
With this bundle you can easy limit requests to your application


Installation
---------
1) Add Zim32RequestLimitBundle to your deps file

    [Zim32RequestLimitBundle]
        git=git://github.com/zim32/Symfony2-RequestLimitBundle.git
        target=/bundles/Zim32/RequestLimitBundle
Make /bin/vendors install

2) Add Zim32RequestLimitBundle to your AppKernel

	$bundles = array(
		.................
		new Zim32\RequestLimitBundle\Zim32RequestLimitBundle(),
	);

3) Add Zim32 namespace into your /app/autoload.php

     $loader->registerNamespaces(array(
         ................
         'Zim32'            => __DIR__.'/../vendor/bundles',
     ));

4) Configure your application. For example

     zim32_request_limit:
       rules:
         rule:
           path: /profile/
           limit: 1
           per: 60
           ip: 192.168.1.2
         some_foo_name:
           path: /
           limit: 10
           per: 1

First rule will limit requests for 1 request per 60 seconds from ip 192.168.1.2 for URL starting with /profile/


Reference
---------

1. path (required) - path to apply rule
2. limit (required) - number of requests. For immediate deny use '0' for limit
3. per (required) - seconds
4. ip (optional) - limit by remote ip

You can use several rules at the same time