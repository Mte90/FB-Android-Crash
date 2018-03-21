# Let's crash the integrated browser in Facebook

First of all integrated in-app browsers suck. 

It's easier for them to track what you read on the web more aggressively and that's not very good.  

Facebook integrated browser is [one of the most used browsers on mobile](https://twitter.com/auchenberg/status/834894652775923712?s=09) and sucks.

### Updates:

* 21/03/2018 - 18:00 UTC: The problem is fixed with the last version of Facebook for Android.

* 22/07/2017 - 13:00 UTC: The problem exists in the last version of Facebook for Android.

* 14/03/2017 - 16:00 UTC: First of all thanks to all the people improved that readme! That repo was shared on [Reddit](https://www.reddit.com/r/webdev/comments/5zbb2d/lets_crash_the_integrated_browser_in_facebook_for/) and on [HackerNews](https://news.ycombinator.com/item?id=13867227) and gettings a little bit of success.

## For developers

Are there any bugs you cannot test because there is no remote debug support and also if you are using Chrome on Android the same issue doesn't happen, probably because they use a different version for something? Like there was for Internet Explorer 6 (sorry to bring back the nightmares) we have no idea how it worked and how to debug in that.  

The only way is to create a HTML file for every test (download the page with `wget -E -H -k -K -p yoururl`), load on a server, create a private group, and share the URL of every version/test. That way we can avoid the caching of Facebook or the app (I have no idea how that works) and have a different version to test and see if Facebook for Android and its integrated browser works.

## What the issue is

Seems that the [WP Rocket](https://wp-rocket.me/) plugin for WordPress with its feature for lazyloading on iframes crashes the browser.  

The behavior is very simple, you open the link from Facebook for Android and the settings to use the external browser is disabled, during the loading of the page this is closed automatically only with an error: "Impossible to open the page".

Anything else, *hasta lasagna!* This is where my nightmare started.  

Before discovering what the problematic feature was, I lost many hours testing in the past few months, but yesterday I decided to find out what the issue was once and for all.

The issue is that the `src` parameter in the iframe does not contain a URL, but a base64-encoded image.

## How to test it

Open this [link](https://www.facebook.com/Mte90/posts/10212614660344107) from Facebook for Android (remember to disable the external browser) and click to the crash page.

## Version affected

As of today (22/07/2017) the last version of Facebook for Android crashes but I worked on that issue in the last months so it is a bug that exist also on old versions of the app.  

The same issue doesn't happen with Facebook for iOS, because they use a different engine.

## Conclusion

There was a time when web developers fought for a free open web that works in the right way (web standards) and was easy to document and debug, but the mobile world is the new battlefield for developers.  

As a Mozillian my suggestion is to fight that using real browsers and create awareness to our customers to use the right browser and not a tiny toy in a black box.
