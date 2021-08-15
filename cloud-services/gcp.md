# GCP

## Firebase

A special version of the google cloud platform that has selected features which provides database, storage, computing and hosting support for Web and Mobile Development.

* [Click here](https://firebase.google.com/docs/guides) to see the Docs.

### Database

* Cloud Firestore
* Realtime Database
  * A simplified version
  * Easy to use

### Cloud Storage

## Google Map

## gtag

* The global site tag \(gtag.js\) is a JavaScript tagging framework and API that allows you to send event data to Google Analytics, Google Ads, and Google Marketing Platform
* [Click](https://developers.google.com/analytics/devguides/collection/gtagjs) to the official developer docs
* gtag methods can be setup in any web app in the header tag of `index.html`, and it can be accessed in all pages if stored as a the window object

  ```markup
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag() {
      dataLayer.push(arguments);
    }
    window.gtag = gtag;
    gtag("js", new Date());
    window.gtag("config", "Target-ID", {
      custom_map: { dimension1: "A", dimension2: "B" },
    });
  </script>
  ```

## Google Analytics

* It can be used to track website activity such as session duration, pages per session, bounce rate etc
* User data can be setup and sent through `gtag.js`

