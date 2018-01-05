---
title: "Chrome 63: The End of .dev for Local Environments"
date: 2018-01-04
layout: Post
cover_index: https://picsum.photos/450?image=1053
tags: [MAMP PRO, MAMP, Google Chrome, Magento]
---
After returning to work from the holiday break, I began to work on a local Magento 1 site that had the TLD *.dev*. I quickly discovered something was wrong. After struggling for about an hour to figure out why Chrome was giving me issues and Safari was not, I learned that since the release of Chrome 63, *.dev* is now redirected to HTTPS via HSTS (HTTP Strict Transport Security) and that was the cause of my problems. In this post I will quickly go over how to update your local Magento 1 site using MAMP. If you want to learn more about this change please visit Mattias Geniar's [article](https://ma.ttias.be/chrome-force-dev-domains-https-via-preloaded-hsts/) on it that goes into more detail.



## 1. Update host name on MAMP

You will want to change the TLD to something else like *.localhost*

![](/images/update-host-name.png)


## 2. Update core_config_data in DB

Next you will want to update the web/unsecure/base_url and web/secure/base_url in the core_config_data table of your database to match the host name in MAMP.

![](/images/update-core-config-data-table.png)



## 3. Clear var folder

Lastly, you will will want to clean your var folder from the *root of your project* with the following command (Do not delete var/log/):

``` bash
$ rm -rf var/cache var/session var/report
```

After that step, you should be able to go back to Chrome and refresh the page with the new TLD, in this case *example.localhost*, and everything should back to normal.

If you have any questions related to this or anything else, feel free to [tweet](https:www.twitter.com/gabepages55) me or shoot me an [email](mailto:gbpages55@gmail.com).
