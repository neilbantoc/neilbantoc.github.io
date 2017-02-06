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

<br />

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

I've always wanted to try out face detection, so for the final project on one of my classes I decided I would do just that. I'm also the type of person who struggles with waking up in the morning, so I thought why not make an alarm clock that uses face detection? I have this tendency of silencing my alarm clock in a matter of seconds then falling directly back to sleep. If I wanted to actually get out of bed, I needed find a way to keep myself awake longer. And what better way for you to wake yourself up than to actually open your eyes.

<br/>

---

<br/>

## Implementation

The point of the project was for us to apply the concepts that we learned from our lectures. I applied 3 main lecture concepts: **Interaction Techniques, Input Events, and Finite State Machines.**

<br/>

### Interaction Techniques

Interaction techniques are software-level tricks that GUI designers use to take a new spin on an existing input device. An example of this would be how the Swype keyboard enhances touchscreen text input with it's gesture typing – it's using the same touchscreen but it can be significantly faster to type on. In my case, I used face detecion as my interaction technique and the front facing camera as my input device. By tracking the user's eye, I can determine if he is falling back to sleep or not and can react accordingly. Eyes open = lowered volume and shorter time needed to keep eyes open. Eyes closed = opposite.

<br />

### Input Events

Input events are a type of abstraction provided by toolkits that make life easier for application developers. Instead of dealing with low-level logic like using time outs for distinguishing between two successive single clicks and a double click, or fiddling with start and end coordinates together with finger veolcity to determine if a touch gesture was a fling or a drag, the toolkit handles all of that and just tells the application developers what happened.

<br />

### Finite State Machine

There are two ways that input devices collect input: **event-based**, where the input device reads input only when the user explicitly makes one (like a button press) and **sampling**, where input is continuously read (like how a smartphone's luminosity sensor that handles auto brightness). Event-based input devices are easier to program with since you just wait for an input event, but for sampled input devices you continuously receive input so you have to filter out information so you get only the ones that you are intersted in.

<br />

<img style="background-color: #ffffff" class="post-image-large center materialboxed responsive-img" src="/images/posts/main/rise-and-smile/fsm.png"/>

<br />
