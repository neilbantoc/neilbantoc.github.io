---
layout: post
title:  "Mobile App: Music Streaming App for MySpace"
thumbnail: /images/posts/thumbs/ilike.gif
categories: dashboard-design, front-end-web, d3, javascript, animation
---
> **Team Size:** 2 people <br/>
**Time Period:** 5 months <br/>
**Role:** Android App Developer <br/>
**Tools:** Eclipse IDE <br/> <br/>
During my early career as an android app developer in the Philippines, I got outsourced by US-based mobile solutions provider Phunware to build a music streaming app for MySpace. It was posed to be a Spotify and Pandora competitor but despite the completion of the mobile apps, the launch did not push through. Nevertheless, I can still highlight some of the design and implementation choices I've maid while building this app.

<br/>

---

<br/>

## Implementation Decisions for Better UX

Choosing a strategy for turning a wireframe into an actual working user interface isn't as simple as one thinks. Do you use built in components that are both reliable and well documented, a library that might be a hit or miss, or write your own? Certain implementation decisions can be easy and fast, which is normally desirable, but may potentially compromise on code maintainability or worse, UX. As an HCI professional, I of course put UX as a high priority.

<br/>

### Decision 1: Using a Sliding Up Panel

<div class="row">
  <div class="small-12 medium-4 post-inline-image-container">

    <img class="post-image-banner materialboxed responsive-img" src="/images/posts/main/ilike/spotify-sliding-up.gif"/>

    <br/>

    <p class="post-image-caption center">Expanding Spotify's mini player is visually boring and ergonomically difficult to perform.</p>

  </div>

  <div class="small-12 medium-8 columns">
    <p class="columns">
    A common thing to see on music players is a mini player on the bottom that you can expand to a full-size one. Spotify's implementation of this on their Android app was less that stellar. From a visual perspective, the transition was pretty boring – it was just a simple cross fade. From a functional/ergonomic perspective, the only way to close the full screen music player was to tap on the minimize icon or Android’s back button, which were on extreme ends on the physical phone.
    </p>
  </div>
</div>

<br/>

<div class="row">
  <div class="small-12 medium-4 post-inline-image-container">

    <img class="post-image-banner materialboxed responsive-img" src="/images/posts/main/ilike/ilike-sliding-up.gif"/>

    <br/>

    <p class="post-image-caption center">Using a Sliding Up Panel is so much better than whatever Spotify is using.</p>

  </div>

  <div class="small-12 medium-8 columns">
    <p class="columns">
    So when I was implementing the same functionality, I made it a point to use a <a href="https://github.com/umano/AndroidSlidingUpPanel">Sliding Up Panel</a>. The upward motion of the sliding panel (that contains the full player), when opened, together with the parallax scrolling of whatever's underneath it, presents a more meaningful transition between the two states. You can also use a  “slide down” gesture anywhere on the panel, providing a bigger touch area compared to tapping a small icon on the far end of the screen.
    </p>
  </div>
</div>

<br/>

### Decision 2: Collapsing Headers

<div class="row">
  <div class="small-12 medium-4 post-inline-image-container">

    <img class="post-image-banner materialboxed responsive-img" src="/images/posts/main/ilike/tripadvisor-collapsing-header.gif"/>

    <br/>

    <p class="post-image-caption center">Headers are an important piece of your UI, but when the user scrolls down, they're probably not as important anymore. So why keep them there?</p>

  </div>

  <div class="small-12 medium-8 columns">
    <p class="columns">
      Headers are useful for displaying information and/or actions that are common for your list. If you have a long list on your app, the user will eventually want to scroll it. Logically, scrolling a list is a signal that they’re interested in the list’s contents, so keeping your header as is and allowing it to take up precious screen real estate isn't really a desirable thing to do.
    </p>
  </div>
</div>

<br/>

---

<br/>

## Added Features

<p>
Next I'll highlight some of the app's features that, present in the original spec sheet or not, I feel add value to the app <i>and</i> were quite the challenge for me as it's the first time I got to implement these features.
</p>

<br/>

### Offline Http Live Streaming

<div class="row">
  <div class="small-12 medium-4 post-inline-image-container">

    <img class="post-image-banner materialboxed responsive-img" src="http://www.streamingmedia.com/Images/ArticleImages/ArticleImage.11612.jpg"/>

    <br/>

    <p class="post-image-caption center">
      HLS, or HTTP Live Streaming, is a popular technology created by Apple where you serve a media stream chunk by chunk over HTTP. In order for me to implement offline HLS, I had to download these chunks onto the device and serve them over HTTP using a webserver running on the device itself.
    </p>

  </div>

  <div class="small-12 medium-8 columns">
    <p class="columns">

      Regular people are probably used to having their music saved as .mp3 files, where individual songs of an album are stored as single .mp3 files and playing a song is just a matter of opening that .mp3 file with a music player. But when you stream songs, one of the popular technologies to use is HLS or HTTP Live Streaming.

      <br/><br/>

      HTTP Live Streaming breaks up your media into chunks of varying qualities and file sizes and serves them accordingly based on your network speed. When I implemented offline HLS, I first had to download these chunks onto the device. Easy enough. But I realized that I can't just point the folder where these chunks are saved to the Android Media Player. In order for it to play the media chunks, I have to serve them over HTTP. And using <a href="https://github.com/NanoHttpd/nanohttpd">nanohttpd</a> I was able to do just that.
    </p>
  </div>
</div>

<br/>

### Controlling Playback Via Bluetooth

<div class="row">
  <div class="small-12 medium-4 post-inline-image-container">

    <img class="post-image-banner materialboxed responsive-img" src="/images/posts/main/ilike/ilike-bluetooth.gif"/>

    <br/>

    <p class="post-image-caption center">
      When you implement lockscreen control support, you're actually indirectly implementing bluetooth support as well.
    </p>

  </div>

  <div class="small-12 medium-8 columns">
    <p class="columns">

      A happy coincidence I had when developing this app was when I added the ability to control music playback using a notification. See when MySpace was desinging the app, they (or at least, the designer they hired) clearly had the iPhone and iOS in mind. They didn't really think of designing a lockscreen notification remote control widget as iOS didn't really support that.

      <br/><br/>

      So I went out of my way and added in a lockscreen notification widget even though it wasn't really something they designed for. When their QA was testing the app, they liked that they were able to control music playback through their car's sound system when connected via bluetooth, which was a pleasant surprise for both me and them.


    </p>
  </div>
</div>

{% include jquery.html %}
{% include materialize.html %}
