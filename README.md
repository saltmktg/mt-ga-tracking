# Google Analytics Tracking Integration

This repository contains pieces of code being used on the Meeting Tomorrow website: http://meetingtomorrow.com

The goal of the code is to attach Google Analytics (GA) tracking parameters to the end of the `src` for several iframes. When the code works, you can "Inspect Element" on the iframe `src`, double-click into the `src` and see something like this (notice the GA tracking parameters placed into the end - things like `custentity_ga_search_medium` and `custentity_ga_search_campaign`):

![iframe screenshot](http://s17.postimg.org/q2w0gc7fz/iframe_screenshot.png)

### The Problem

The problem is that the code we're using to do this *doesn't* work in Internet Explorer. It only works in Chrome, Firefox, and Safari - but no IE. Since 15-20% of the site's visitors use Internet Explorer, it needs to work for those users as well.

### About the Code

The original code comes from this blog post here: http://cutroni.com/blog/2009/03/18/updated-integrating-google-analytics-with-a-crm/

We've adapted it to fit our site, and we're also using it to append the GA tracking parameters to the `src` of at least 2 different iframes on the same page - and sometimes 3 different iframes. For example, look at this page here: http://meetingtomorrow.com/contact On this page there are 3 iframes (which are used to display 3 different forms):

1. The main form in the middle of the page
2. If you click the "Request a Free Quote" sidetab, you'll see another form (i.e. iframe)
3. If you visit the site for the first time (or in Chrome's "Incognito Mode"), and move your cursor into the browser bar at the top, you'll see an Exit Intent form appear. This is also another separate iframe.

##### How the Code Works
Check out [tracking-code-isolated.html](https://github.com/saltmktg/mt-ga-tracking/blob/master/tracking-code-isolated.html) to see the main snippet of code. In essence, what it's doing is grabbing GA tracking cookies from the visitor, and then dumping them into hidden fields, which get populated into the iframe `src`. This gets triggered by a line of code (line 1409 in [header.php](https://github.com/saltmktg/mt-ga-tracking/blob/master/header.php)): ```<body onload="populateHiddenFields(document.forms['ga-tracking-form'])">```

##### Not Working in Internet Explorer

Once again, this all works how we want it to - *except in Internet Explorer*. For whatever reason, in IE, the GA tracking parameters don't get thrown onto the end of the iframe `src`. **This is where we need help.** We need someone to get the GA tracking parameters to populate at the end of each form's iframe `src` in Internet Explorer. For testing purposes, if you can get it to work on each form's iframe on the following pages in IE, we should be in good shape:

- http://meetingtomorrow.com/nationwide-rentals
- http://meetingtomorrow.com/contact
- http://meetingtomorrow.com/chicago-audio-visual-rentals

##### Questions & Feedback

Please direct questions or comments on the project to rkarpeles[at]saltdigitalmarketing.com