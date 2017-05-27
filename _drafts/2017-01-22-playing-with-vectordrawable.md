---
layout: post
title:  "Playing with VectorDrawable"
categories: android, ui, vector-drawable
---

In a recent experiment to make the freelancer.com app's ProjectViewPage more <a href="https://www.google.com/design/spec/material-design/introduction.html" target="_blank">Material Designed</a>, I've decided to change certain parts of the existing implementation to include more material interactions. You can find an overview of how I'm making the ProjectViewPage more material in <a href="https://imbantman.wordpress.com/2015/12/25/material-redesign-adventures-1-freelancer-project-view-page/">this post</a>, but for this post, I'll be focusing on how I created the morphing icon that toggles the visibility of the BidStatistics.

<h1>The Goal</h1>
I've always wanted to create a button that exhibited <a href="https://www.google.com/design/spec/animation/delightful-details.html">delightful</a><a href="https://www.google.com/design/spec/animation/delightful-details.html" target="_blank"> details</a>, so I decided to make use of a <code>VectorDrawable</code> so that I can morph my icon from one state to the other. Since the button's purpose is to show and hide the BidStatistics, I went with a line graph icon to indicate that the button's action is related to statistics, in this case, showing the bid statistics of the currently shown project. When the BidStatistics are visible, the button's purpose changes from showing to hiding them. To communicate this to the user, I used an X icon to indicate a close action.

 

[caption id="attachment_220" align="aligncenter" width="743"]<img class="alignnone size-full wp-image-220" src="https://imbantman.files.wordpress.com/2015/12/screen-shot-2015-12-06-at-9-36-32-pm.png" alt="Screen Shot 2015-12-06 at 9.36.32 PM.png" width="743" height="356" /> Left: Graph Icon, Right: Close Icon[/caption]

The end goal is to be able to morph the lines that make up the graph icon into the lines that make up the close icon, as illustrated here:

[caption id="attachment_227" align="aligncenter" width="179"]<img class=" size-full wp-image-227 aligncenter" src="https://imbantman.files.wordpress.com/2015/12/ezgif-com-optimize.gif" alt="ezgif.com-optimize.gif" width="179" height="176" /> It's morphing time![/caption]

Since VectorDrawable is a new api introduced in Lollipop, in order to provide backwards compatibility, we'll be using <a href="https://github.com/wnafee/vector-compat" target="_blank">VectorCompat</a>.

The road to achieving this is a long one. How long, you ask? Well here's a list of all of the things we need:

In res/strings.xml:
<ul>
	<li>Vector path data for graph icon</li>
	<li>Vector path data for close icon</li>
</ul>
In res/drawable:
<ul>
	<li>ic_vector_graph - a static vector drawable for the graph icon</li>
	<li>ic_vector_close_2 - a static vector drawable for the close icon (the 2 is there because I have another close vector drawable compatible with a different icon)</li>
</ul>
In res/anim:
<ul>
	<li>graph_to_close_2_path - an ObjectAnimator that animates the path values from the graph icon to the close icon</li>
	<li>close_2_to_graph_pah - an ObjectAnimator that animates the path values from the close icon to the graph icon</li>
</ul>
And finally, in res/drawable again:
<ul>
	<li>ic_graph_to_close_2 - an animated vector drawable that animates the graph icon into the close icon</li>
	<li>ic_close_2_to_graph - an animated vector drawable that animates the close icon to the graph icon</li>
</ul>
So, let's get started, shall we?
<h1>Creating the Vector Images</h1>
First let's try creating the two icons using SVG. I've used <a href="http://svg-edit.googlecode.com/svn-history/r1771/trunk/editor/svg-editor.html" target="_blank">a free online SVG </a>editor because I'm too lazy to download an offline one, but you can use any editor you want, like <a href="https://inkscape.org/en/" target="_blank">InkScape</a>, for example.

Before getting started, I recommend doing the following to make your drawing easier:
<ol>
	<li>Change document size to icon dimensions, like 60 x 60</li>
	<li>Turn on the guideline grid</li>
</ol>
<h2>The Graph Icon</h2>
Let's create the first drawable, the graph icon.
<ol>
	<li>Start by creating the axes  by plotting 3 points using the path tool.</li>
	<li>After drawing the axes, plot the line graph next using 4 points</li>
</ol>
The result should be something like below:

[gallery ids="243,244" type="rectangular"]

Good. Let's now extract the path data points from the resulting SVG Image. Click on the "view SVG source" button on the top left to get access to the SVG source. You should be able to see two <code><path/></code> elements, one for each path we drew previously. The path data points can be found in the <code>d=""</code> attribute of the path. We'll be joining these two path elements into one because both of these paths are involved in the same animation, so cut the values from both paths and save them as a string resource.

[code language="xml"]
<string name="freelancer_pvp_path_graph">
        M5.47108,4.98545l-0.03946,49.52474l49.56354,-0.09807
        M10.41707,49.60228l9.56354,-24.28707l14.64597,18.91367l14.83994,-34.14159</string>
[/code]
Note that I've changed the small m from the SVG editor into a big M when I saved the path data to a string resource. Since I'm combining the two subpaths into one string, using the relative move command (small m) will mess up the path drawing so you'll need to use the absolute move command (big M) to solve this problem. If you are not familiar with the SVG path drawing commands (M, L, Z), I recommend familiarizing yourself with the basics.
<h2>The Close Icon</h2>
Now, creating the close icon isn't as simple as drawing two straight lines  and calling it a day. I'll explain why later, but for now, let's start by duplicating the current layer we're in so that we can have an exact copy of what we've drawn so far. Hide the old layer for safekeeping.

[caption id="attachment_294" align="aligncenter" width="288"]<img class=" size-full wp-image-294 aligncenter" src="https://imbantman.files.wordpress.com/2015/12/screen-shot-2015-12-06-at-9-26-26-pm.png" alt="Screen Shot 2015-12-06 at 9.26.26 PM.png" width="288" height="354" /> Create a new layer and name it close[/caption]

Next, rearrange the vertices of the axes and the line graph into the shape of an X. As you can see below, the vertices fall in a straight line, appearing to be a single line when they are in fact made up of multiple smaller ones.

<img class="alignnone size-full wp-image-298" src="https://imbantman.files.wordpress.com/2015/12/screen-shot-2015-12-06-at-9-26-04-pm.png" alt="Screen Shot 2015-12-06 at 9.26.04 PM.png" width="1248" height="1250" />

Same as the graph icon, save the data points you got from the SVG source into a string resource.

[code language="xml"]
<string name="freelancer_pvp_path_close2">
        M5.47108,4.98545l24.59682,24.98545l24.9273,24.4412
        M5.47041,54.64591l14.51019,-14.49079l20.17457,-20.36852l14.45197,-14.45199</string>
[/code]
<h1>Static Vector Drawables from Path Data</h1>
Now that we have path data for our two icons, we can now define a <code>VectorDrawable</code> resource that can parse the path data into a handy <code>Drawable</code> we can use for our backgrounds, buttons, etc.

Create a resource file in res/drawable and name it <code>ic_vector_graph</code>. Here's what we'll be putting into that file:

[sourcecode language="xml"]
<?xml version="1.0" encoding="utf-8"?>
<vector xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:width="24dp"
    android:height="24dp"
    android:viewportHeight="60"
    android:viewportWidth="60"

    app:vc_viewportHeight="60"
    app:vc_viewportWidth="60"
    tools:targetApi="lollipop">

    <path
        android:name="v"
        android:fillColor="#00000000"
        android:strokeColor="#ffffff"
        android:strokeWidth="4"
        android:pathData="@string/freelancer_pvp_path_graph"

        app:vc_fillColor="#00000000"
        app:vc_strokeColor="#ffffff"
        app:vc_strokeWidth="4"
        app:vc_pathData="@string/freelancer_pvp_path_graph" />

</vector>
[/sourcecode]
Let's create another resource file for the close icon. In res/drawable, create another file called ic_vector_close_2 with the following contents:

[sourcecode language="xml"]
<?xml version="1.0" encoding="utf-8"?>
<vector xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:width="24dp"
    android:height="24dp"
    android:viewportHeight="60"
    android:viewportWidth="60"

    app:vc_viewportHeight="60"
    app:vc_viewportWidth="60"
    tools:targetApi="lollipop">

    <path
        android:name="v"
        android:fillColor="#00000000"
        android:strokeColor="#ffffff"
        android:strokeWidth="4"
        android:pathData="@string/freelancer_pvp_path_close2"

        app:vc_fillColor="#00000000"
        app:vc_strokeColor="#ffffff"
        app:vc_strokeWidth="4"
        app:vc_pathData="@string/freelancer_pvp_path_close2" />

</vector>
[/sourcecode]
Here I've defined a <code><vector/></code> resource with one <code><path/></code> element that uses the path data we saved earlier. This is actually already a drawable that you can use as is in xml: <code>android:background="@drawable/ic_vector_graph"</code> or in java: <code>getResources().getDrawable(R.drawable.ic_vector_graph)</code>

Note that there are two versions of the xml attributes: one prefixed by <code>android:</code> and another prefixed by <code>app:vc_</code>. This is done for backwards compatibility - the ones using the android namespace will be used by the lollipop version of vector drawables while the app:vc_ ones will be used by VectorCompat.

Another thing to note is the value for the viewport width and height. Since I used a 60 x 60 drawing canvas, that's the value I entered in the xml, but theoretically, you can have a 1 x 1 viewport and define values ranging from 0-1 like 0.5, 0.75, etc. That's the magic of vector drawables - they scale accordingly.

The last thing to note is the <code>android:name=""</code> attribute. This is used to label paths so that you can target specific paths with different kinds of animations. This is useful for more complex animations, but for our example, we have only one path and one animation so we'll ever only going to use that attribute once.
<h1>Morphing Between Drawables</h1>
Now that we have static vector drawables, we can now proceed to animating them. As a general overview, morphing between two drawables is achieved by using an ObjectAnimator to animate the path of two VectorDrawables. This is why it is important that the <code>pathData=""</code> attribute of your <code><path></code> elements have the same number of commands. Aside from having the same amount of commands, each command type must have a corresponding command of the same type in the same order.

[caption id="attachment_541" align="aligncenter" width="671"]<img class=" size-full wp-image-541 aligncenter" src="https://imbantman.files.wordpress.com/2016/01/screen-shot-2016-01-07-at-12-49-29-pm.png" alt="Screen Shot 2016-01-07 at 12.49.29 PM.png" width="671" height="103" /> Two vector paths with 2 move commands each - an example of compatible vector drawables.[/caption]

So, let's go ahead and create those animators, shall we?
<h2>The Animators</h2>
First, for morphing the graph icon into the close icon, let's create a file called <code>graph_to_close_2_path</code> in /res/anim and fill it up with this:

[sourcecode language="xml"]
<?xml version="1.0" encoding="utf-8"?>
<objectAnimator xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:duration="@integer/anim_duration"
    android:propertyName="pathData"
    android:valueFrom="@string/freelancer_pvp_path_graph"
    android:valueTo="@string/freelancer_pvp_path_close2"
    android:valueType="pathType"
    app:vc_valueType="pathType" />
[/sourcecode]
Then for the reverse, let's create <code>ic_close_2_to_graph_path</code>:

[sourcecode language="xml"]
<?xml version="1.0" encoding="utf-8"?>
<objectAnimator xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:duration="@integer/anim_duration"
    android:propertyName="pathData"
    android:valueFrom="@string/freelancer_pvp_path_graph"
    android:valueTo="@string/freelancer_pvp_path_close2"
    android:valueType="pathType"
    app:vc_valueType="pathType" />
[/sourcecode]
Which is pretty much the same as the first one with the values of valueFrom and valueTo interchanged.
<h2>The Animated Vector Drawables</h2>
Finally, we can write our animated vector drawables.

Start with creating <code>ic_graph_to_close_2</code> in res/drawable:

[sourcecode language="xml"]
&lt;xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;animated-vector xmlns:android=&quot;http://schemas.android.com/apk/res/android&quot;
    xmlns:tools=&quot;http://schemas.android.com/tools&quot;
    android:drawable=&quot;@drawable/ic_vector_graph&quot;
    tools:targetApi=&quot;lollipop&quot;&gt;

    &lt;target
        android:name=&quot;v&quot;
        android:animation=&quot;@anim/graph_to_close_2_path&quot;&gt;;
&lt;/animated-vector&gt;
[/sourcecode]
And the corresponding reversed version, <code>ic_close_2_to_graph</code> in the same folder:

[sourcecode language="xml"]
&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;animated-vector xmlns:android=&quot;http://schemas.android.com/apk/res/android&quot;
    xmlns:tools=&quot;http://schemas.android.com/tools&quot;
    android:drawable=&quot;@drawable/ic_vector_close_2&quot;
    tools:targetApi=&quot;lollipop&quot;&gt;

    &lt;target
        android:name=&quot;v&quot;
        android:animation=&quot;@anim/close_2_to_graph_path&quot; /&gt;
&lt;/animated-vector&gt;
[/sourcecode]
The animated vector object is simply a list of mappings between animations and the corresponding paths where the animations will be applied to.

Now that we have our animated vector drawables ready, we can now use them in any android widget! Though if you use normal widgets, you'll have to manually start the animation. For convenience though, you can use a <code>MorphButton</code>, like so:

[sourcecode language="xml"]
&lt;com.wnafee.vector.MorphButton
    android:id=&quot;@+id/morph_button&quot;
    android:layout_width=&quot;wrap_content&quot;
    android:layout_height=&quot;48dp&quot;
    android:layout_gravity=&quot;right&quot;
    android:layout_marginRight=&quot;8dp&quot;
    android:padding=&quot;8dp&quot;
    app:vc_endDrawable=&quot;@drawable/ic_close_2_to_graph&quot;
    app:vc_startDrawable=&quot;@drawable/ic_graph_to_close_2&quot; /&gt;
[/sourcecode]
The morph button automatically detects if the background it has is animatable and plays the animation automatically.
