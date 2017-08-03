# DOM Lifecycle events
I am obsessed with page load speed, website performance, and just about anything that is tangentially related to improving the user experience of my website(s).

I created this repo as a place to make sense of all the metrics, measurements, and industry standards around web page speed and performance.  I'm sure there are other resources online that will tell you the same as is listed here but I wanted to create an all-in-one place for myself, for future reference.

### History Lesson
Back in the day (Web 1.0 days) the `window.onload()` event was a great measurement for how long it took for a page to fully render because it is a standard event implemented across all browsers and it reflected the actual user perception since web pages were very static. This was the official proxy for time-to-interactive (tti).  Said another way, `.onload()` is based on a page's resources downloading and in the old days of simple text and small images, the page's readiness was closely tied to its resources downloading.

### Today
In the world of dynamic content loading, single page apps, plentiful network requests, etc, `.onload()` is no longer an accurate measurement of a user's perception that the page has rendered and ready to be interacted with.  As a specific example, read [this article](http://www.stevesouders.com/blog/2013/05/13/moving-beyond-window-onload/) of how Amazon's above-the-fold content loads much faster than the `.onload()` timestamp.  We need something better to truly measure the time-to-interactive (TTI).

### How to Measure Time-to-Interactive (TTI)
TTI is a very important metric to measure because it represents the time it takes for the page to become interactive _from the perspective of the user_ and not necessarily when the page is officially done loading.  That's an important distiction -- we care about _perceived_ loading time vs. actual loading time.  So exactly can we measure TTI?


### TODO TTI discussion
- need a section about how companies are measuring TTI and how strategies differ among clientside JS frameworks

### TODO additional notes
- possibly discuss corner cases like lazy loading, above/below the fold content, etc

### Navigation Timing API
Most browsers now provide a performance timing API ([source](https://developer.mozilla.org/en-US/docs/Web/API/Navigation_timing_API)).  The `window.peformance.timing` events fire in the following order.  Using these timestamps (ms) of each of these, you can calculate time-to-interactive(TTI):
  - navigationStart
  - fetchStart
  - domainLookupStart
  - domainLookupEnd
  - connectStart
  - secureConnectionStart
  - connectEnd
  - requestStart
  - responseStart
  - responseEnd
  - domLoading
  - domInteractive
  - domContentLoadedEventStart
  - domContentLoadedEventEnd
  - loadEventStart
  - domComplete
  - loadEventEnd

TODO: extract descriptions from here and compare to DOM events: https://developer.mozilla.org/en-US/docs/Web/API/PerformanceTiming

TODO: add back missing events from list above

### index.js

- TODO remove comments from index.js and place here

- to see the logs fire under slow internet, make sure to throttle your network in the chrome dev tools network tab.  that way you can see how the jquery script attributes and placement affect user experience.
- comment / uncomment the jquery scripts to see effects
