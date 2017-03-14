#Let's crash the integrated browser in Facebook

First of all integrated browser in app sucks.  
It is easy for them to track more aggressively what do you read on the web and is not very good.  
Facebook integrated browser is one of the most [used browser on mobile](https://twitter.com/auchenberg/status/834894652775923712?s=09) and sucks.

##For developers

If there are bugs you cannot testing because there is no remote debug support and also if you are using Chrome on Android the same issue cannot happen, probably because they use a different version for something. Like there was for Internet Explorer 6 (sorry for the nightmares) we have no idea how works and how to debug in that.   
The only way is to create an html file for every test (download with `wget -E -H -k -K -p yoururl` the page), load on a server, create a private group, and here share the url of every version/test. In that way we can avoid the caching of Facebook or of the app (I have no idea how to works) and have different version to test and see if Facebook for Android and is integrated browser works.

##What is the issue

Seems that the [WP Rocket](https://wp-rocket.me/) plugin for WordPress with his feature for lazyload on iframe let's crash the browser.  
The behaviour is very simple, you open the link from Facebook for Android and the settings to use the external browser is disabled, during the loading of the page this is closed automatically only with an error: "Impossible open the page".  
Anything else, Hasta lasagna! Now it is where my nightmare is started.  
Before to discover that was that feature I lost many hours in the past months to testing but yesterday I chosen to find the issue definitely.  
The issue is the `src` parameter in the iframe that not contain a URL but an image in base64.

##How to test it

Open this [link](https://www.facebook.com/Mte90/posts/10212614660344107) from Facebook for Android (remember to disable the use external browser) and click to the crash page.

##Version affected

At today (14/03/2017) the last version of Facebook for Android crash but I worked on that issue in the last months so it is a bug that exist also on old versions of the app.  
The same issue doesn't happen on Facebook for iOS because they use a different engine.

##Conclusion

There was a time where web developers fight for a free open web that works in the right way (web standards) and was easy to docuemnt and debug it but the mobile world is the new battlefield for developers.  
As a Mozillian my suggestion is to fight that using real browser and create awareness to our customers to use the right browser and not a tiny toy in a black box with no button.
