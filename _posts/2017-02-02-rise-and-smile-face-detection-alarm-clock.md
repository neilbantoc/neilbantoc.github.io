---
layout: post
title:  "Rise and Smile: Face Detection Powered Alarm Clock"
thumbnail: /images/posts/thumbs/rise-and-smile.gif
categories: android, face-detection
---

> **Role:** Prototyper/Mobile Application Developer <br /> **Tools and Libraries:** Android Studio, Google Play Services (for face detection) <br/> **GUI Programming Concepts:** Input devices, input events, finite state machine, model-view-presenter for Android
<br /> <br/> This was a final requirement for Software Structures for User Interfaces, a core subject I took when I was completing my Master’s degree in Human-Computer Interaction from Carnegie Mellon University. Parts of the code from the googly-eyes sample were used in this project.

{% include jquery.html %}
{% include materialize.html %}

<br />

## Introduction

<div class="row">

  <div class="small-12 medium-4 post-inline-image-container">

    <img class="post-image-large" src="/images/posts/main/rise-and-smile/rise-and-smile.gif"/>

  </div>

  <p class="columns">An alarm clock that wakes you up by using face detection to force you to keep your eyes open. Sounds crazy? What if I told you that it also takes snapshots of you while you struggle to wake up, keeping them hostage and potentially posting them to social media (with the hashtag <strong>#wokeuplikethis</strong>, of course) if you hit snooze or fail to wake up? Let’s see if that doesn’t make you want to wake up.</p>

</div>

<br />

---

<br/>

## Motivation

<div class="row">

  <div class="small-12 medium-4 post-inline-image-container">

    <img class="post-image-large" src="/images/posts/main/rise-and-smile/alarms.png"/>

  </div>

  <p class="columns">I've always wanted to try out face detection, so for the final project on one of my classes I decided I would do just that. I'm also the type of person who struggles with waking up in the morning. I have this tendency of silencing my alarm clock in a matter of seconds then falling directly back to sleep. So I thought why not make an alarm clock that uses face detection? If I wanted to actually get out of bed, I needed find a way to keep myself awake longer. And what better way for you to wake yourself up than to actually open your eyes for a long time.</p>

</div>

<br/>

---

<br/>

## Implementation

The point of the project was for us to apply the concepts that we learned from our lectures. I applied 3 main lecture concepts: **Interaction Techniques, Input Events and Finite State Machines.**

<br/>

### Interaction Techniques

<div class="row">

  <div class="small-12 medium-4 post-inline-image-container">

    <img class="post-image-banner" src="http://beebom.redkapmedia.netdna-cdn.com/wp-content/uploads/2015/12/iOS-Keyboards-bb-Swype.jpg"/>

  </div>

  <p class="columns">Interaction techniques are software-level tricks that GUI designers use to take a new spin on an existing input device. An example of this would be how the Swype keyboard enhances touchscreen text input with it's gesture typing – it's using the same touchscreen but it can be significantly faster to type on.
  <br /> <br />
  In my case, I used face detection as my interaction technique and the front facing camera as my input device. By tracking the user's eye, I can determine if he is falling back to sleep or not and can react accordingly. If his eyes are open, that means he's awake so I lower the volume and start the countdown timer. If his eyes are closed or if his face is missing, I reset the volume and timer back to 100%. </p>

</div>

<br />

### Input Events

<img style="background-color: #ffffff" class="post-image-large center materialboxed responsive-img" src="/images/posts/main/rise-and-smile/gestures.png"/>

Input events are a type of abstraction provided by toolkits that make life easier for application developers. You see for button-type events like mouse clicks, it's fairly easy to determine if the user made a right click or a left click. There are however more complicated input devices that may generate noisy data, hard to analyze data, or both. Touchscreen gestures are a great example of this: think about it, what distinguishes a tap and drag from a fling/flick event? Velocity. A tap and drag has low velocity while the opposite is true for fling events. You'd have to take in x and y coordinates together with deltas (change over time) to determine that.

For my case, the camera was feeding me continuous frames of faces, each with a probability of whether or not the eyes are closed or not. Using a finite state machine, I was able to abstract these into three simple input events: EYE_OPEN, EYE_CLOSED and FACE_MISSING.

<br />

### Finite State Machine

My interaction technique involved handling 3 states: open eyes, closed eyes, and face missing. Like any UI component, it's best to create a finite state machine to make it easier to handle input. Mine ended up looking like this:

<br />

<img style="background-color: #ffffff" class="post-image-large center materialboxed responsive-img" src="/images/posts/main/rise-and-smile/fsm.png"/>

I used this finite state machine to determine when to send out input events, that is, whenever there is a state transition.

<br />

---

<br />

### Initial Prototype and Nielsen's Heuristics

<div class="row">

  <div class="small-12 medium-4 post-inline-image-container">

    <img style="background-color: #ffffff" class="post-image-large center materialboxed responsive-img" src="/images/posts/main/rise-and-smile/prototype.png"/>

  </div>

  <p class="columns">The initial prototype I made had two circular rings that represent volume and the awake countdown. I was hoping that this setup was intuitive enough for my testers since I thought having the rings react to blinking was enough <a href="http://www.mattsoave.com/old/cogs187a/iu_site_eval/1visibility.html">feedback for them to determine what's happening.</a> Apparently, it wasn't. They get the feedback, but they <a href="http://www.mattsoave.com/old/cogs187a/iu_site_eval/2systemreal.html">don't know what that feedback meant.</a> So I had to think of a way to convey to the user that one ring represents the volume level and the other is tracking whether or not their eyes were open.</p>

</div>

<br/>

### Final Prototype and Future Improvements

<div class="row">

  <div class="small-12 video-container">

    <iframe width="560" height="315" src="https://www.youtube.com/embed/EJEMnHAsoSc" frameborder="0" allowfullscreen></iframe>

  </div>

  <div class="columns"> <br/> <p>The final prototype wasn't a huge departure from the original design. I incorporated the feedback from the initial prototype and added icons to better indicate what the progress circles meant and also added a help button as a fallback in case users are completely clueless. </p>
  <br/>
  <p>Some of the future improvements I'm considering to add are:</p>
  <ul style="list-style: none;">
    <li><p>Capturing frames and uploading to social media</p></li>
    <li><p>Changing alarm tones</p></li>
    <li><p>Repeating alarms</p></li>
    <li><p>Setting alarms upon booting</p></li>
  </ul>
  </div>

</div>
