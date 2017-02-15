---
layout: post
title:  "Rise and Smile: Face Detection Powered Alarm Clock"
thumbnail: /images/posts/thumbs/rise-and-smile.gif
categories: android, face-detection
---

> **Role:** Prototyper/Mobile Application Developer <br /> **Tools and Libraries:** Android Studio, Google Play Services (for face detection) <br/> **GUI Programming Concepts:** Input devices, event handling, model-view-presenter for Android
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

The point of the project was for us to apply the concepts that we learned from our lectures. I applied 3 main lecture concepts: **Interaction Techniques, Finite State Machines, and Input Events.**

<br/>

### Interaction Techniques

Interaction techniques are software-level tricks that GUI designers use to take a new spin on an existing input device. An example of this would be how the Swype keyboard enhances touchscreen text input with it's gesture typing – it's using the same touchscreen but it can be significantly faster to type on.

In my case, I used face detecion as my interaction technique and the front facing camera as my input device. By tracking the user's eye, I can determine if he is falling back to sleep or not and can react accordingly. If his eyes are open, that means he's awake so I lower the volume and start the countdown timer. If his eyes are closed or if his face is missing, I reset the volume and timer back to 100%.

<br />

### Finite State Machine

My interaction technique involved handling 3 states: open eyes, closed eyes, and face missing. Like any UI component, it's best to create a finite state machine to make it easier to handle input. Mine ended up looking like this:

<br />

<img style="background-color: #ffffff" class="post-image-large center materialboxed responsive-img" src="/images/posts/main/rise-and-smile/fsm.png"/>

I used this finite state machine to determine when to send out input events, that is, whenever there is a state transition.

<br />

### Input Events

Input events are a type of abstraction provided by toolkits that make life easier for application developers. Instead of dealing with low-level logic like using time outs for distinguishing between two successive single clicks and a double click, or fiddling with start and end coordinates together with finger veolcity to determine if a touch gesture was a fling or a drag, the toolkit handles all of that and just tells the application developers what happened.



<br />
