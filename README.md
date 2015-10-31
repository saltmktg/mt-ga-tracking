# Google Analytics Tracking Integration

This repository contains pieces of code being used on the Meeting Tomorrow website: http://meetingtomorrow.com

The goal of the code is to attach Google Analytics (GA) tracking parameters to the end of the `src` for several iframe URLs. When the code works, you can "Inspect Element" on the iframe `src`, double-click into the `src` and see something like this (notice the GA tracking parameters placed into the end of the URL - things like `custentity_ga_search_medium` and `custentity_ga_search_campaign`):

![iframe screenshot](http://s17.postimg.org/q2w0gc7fz/iframe_screenshot.png)

### The Problem

The problem is that the code we're using to do this *doesn't* work in Internet Explorer. It only works in Chrome, Firefox, and Safari - but no IE. And since 15-20% of the site's visitors use Internet Explorer, it needs to work for them.

### About the Code

The original code comes from this blog post here: http://cutroni.com/blog/2009/03/18/updated-integrating-google-analytics-with-a-crm/

We've adapted it to fit our site, and we're also using it to append the GA tracking parameters to at least 2 different iframes on the same page - and sometimes 3 different iframes. For example, look at this page here: http://meetingtomorrow.com/contact  On this page there 3 iframes (which are used to display forms):

- The main form in the middle of the page
- If you click the "Request a Free Quote" sidetab, you'll see another form (i.e. iframe)
- If you visit the site for the first time (or in Chrome's "Incognito Mode"), and you move your cursor into the browser bar at the top, you'll see an Exit Intent form appear. This is also another separate iframe.









Original source code: 

Body onload 
