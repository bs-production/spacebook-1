---
title: Guidelines
date: 2020-11-20
permalink: /guidelines/index.html
eleventyNavigation:
  order: 10
  key: Guidelines
---
## No Longer Dealer 

1.  **CMS > Site Content > Site Template > Borders tab**  
Replace all existing code in `Borders` tab with below PHP snippet along with "The requested page is unavailable."  
Make sure it's pushed live.  
```php
<?php
header("HTTP/1.0 503 Service Unavailable");
?>
The requested page is unavailable. 
```

2. **CMS > Site Content > Content Management > Home page**  
Delete the contents of the `Home` page.  
Make sure to push it live.

3. **CMS > Site Content > Site Rewrites > Advanced Rewrites tab**  
Replace any existing redirects in the text box with `/(.+) /`

4. Navagate to the site's home page and refresh with `?cache=0`  
Page should display nothing but `The requested page is unavailable.`




## Backups & Redirects 

Mac - [Site Sucker](http://ricks-apps.com/osx/sitesucker/)

Windows - [HTTrack](https://www.httrack.com/)

Use one of the above programs to download a backup of the site you are currently working on. When you are done please place folder in the Marketing Drive in the folder Site Backups. 

Please make sure the folder is domain.com



### Wayback download 

If you need to grab something from wayback machine. This works really well 

https://github.com/hartator/wayback-machine-downloader

```
wayback_machine_downloader http://brandywineexteriors.com --to 20150427070206 --directory ~/Downloads/brandy
```

***
### Site Rewrites 

 /(.+) /  - Redirect Everything to the homepage 

 (.+) http://www.domain.com/  - Redirect everything every to an external domain. 
 
 ^/testimonials.html /about-us/testimonials.html - Redirect top level page to subdirectory without looping

/roof-repair/(.+) /about-us/$1 - Redirects pages inside one subdirectory to another subdirectory 

/roof-repair/(.*) /about-us/$1 - Redirects pages inside one subdirectory to another subdirectory

^/siding/$ /siding.html - Redirects exact match of string without affecting interior page URLs
***
### PHP Status Codes

```php
<?php
header("HTTP/1.0 404 Page Not Found");
?>
The requested page has not been found.
```

```php
<?php
header("HTTP/1.0 410 Gone");
?>
The requested page has been removed.
```

```php
<?php
header("HTTP/1.0 503 Service Unavailable");
?>
The requested page is unavailable.
```


### Payment Issue 
No status code and just redirect to coming soon page. 




### BBB 

#### Follow steps to get code for BBB seal
1. Google to find the bbb.org page for your dealer *(ex. Google 'BBB Adam Quenneville')*
2. Once you've reached the dealer's 'BBB BUSINESS REVIEW' page, copy the company id at the end of the site's url 
3. Visit <a href="http://www.bbb.org/online/business/dynamicseal.aspx" target="_blank">http://www.bbb.org/online/business/dynamicseal.aspx</a>
4. Paste company id
5. Select BBB territory
6. Login and choose seal options
7. Once you've selected a choice for every option, copy the outputted code
8. Throw code wherever needed on your site!