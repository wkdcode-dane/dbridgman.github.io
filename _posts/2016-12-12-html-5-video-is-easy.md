---
layout: post
title:  "HTML5 Video - It's actually pretty simple!"
date:   2016-12-12
---

**So I remember the days when adding video content to your page was never really straightforward. Usually you'd be relying on video platforms, plugins, and other sorts of embedables that you'd have to resort to using to get your videos going. Not only that, but the end content used to be something like those now cringe worthy video presenters that would appear out of a virtual door onto your screen. What was normal then, just seems totally surreal now!**

Video presenters aside - I was recently tasked with adding some videos to a clients website the other week. Back in the day this would have been a little bit of a chore, grabbing a video player like JW Player and clawing around for the companies license key. Thankfully though these days are a thing of the past, with HTML5 landing on the scene absolutely years ago - it's certainly a real safe bet to be using the HTML5 `<video>` tag these days. All modern browsers support this tag, and it's only when you hit IE8 when you start to hit issues.

To get everything working, pretty much all you need to do is have your video file ready to roll, and it's almost as easy as adding an image to a page:

{% highlight html %}

<video src="assets/video/my-awesome-video.mp4" controls>
</video>

{% endhighlight %}

The code above will simply add the video to the page, and display the first frame with some browser default controls. There are a shed tonne of customisable attributes you can attach to the tag that make fine tuning everything that much easier, many of which are totally self explanatory. So say I want my video to automatically play? Easy, `autoplay`. How about loop when the video has finished? Fine, `loop`. Want your users to have control over the video? Excellent `controls`. Essentially all the tools you need are pretty much there to get you going. A quick skim through <a href="https://developer.mozilla.org/en/docs/Web/HTML/Element/video" target="\_blank">MDN</a> will reveal a nice list that is well worth a browse and documents each attribute in detail.

{% highlight html %}

<video src="assets/video/my-awesome-video.mp4" width="100%" autoplay controls>
</video>

{% endhighlight %}

The code above spews out what you'll see below:
<p></p>
<video src="assets/video/sea-scape.mp4" width="100%" autoplay controls>
</video>

## Lets make this interesting!

So adding a plain video is easy enough, but lets take it up a notch! One major advantage of using HTML5 video is the fact that the markup is on your page to do whatever you like with. Meaning it can be easilly manipulated with CSS and Javascript, so styling it up ends up being trivially simple, since it's essentially like styling any other block on a page. You can do anything from making your own controls, overlays, hell even the current trend... background videos!


{% highlight html %}

<style>
  video {
    position: fixed;
    top: 50%;
    left: 50%;
    min-width: 100%;
    min-height: 100%;
    width: auto;
    height: auto;
    z-index: -1;
    transform: translateX(-50%) translateY(-50%);
  }
  .background-overlay {
    font-family:monospace;
    background-color:black;
    position:absolute;
    width:100%;
    height:100%;
    top:0;
    left:0;
    opacity:0.4;
  }
  h1 {
    font-family: sans-serif;
    color:white;
    top: 50%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%);
    position:absolute;
    border: 1px solid;
    padding:1rem 2rem;
    box-sizing:border-box;
  }
</style>

<video src="http://www.dbridgman.co.uk/assets/video/sea-scape.mp4" autoplay loop mute>
</video>

<div class="background-overlay">
</div>

<h1>Look at my super awesome video background!</h1>

{% endhighlight %}

So lets take a look at the code above, all I've done is add the video to the page minus any controls and playing on loop. I threw a background overlay over the top to dull the vibrancy a little bit and make text a little easier to read, using `<div>` overlays as a make shift filter can also be really effective if you have a poor quality video that's a little pixelated that you want to mask a little bit. The output of the code above can be seen in the code pen below:
<p></p>
<p data-height="265" data-theme-id="0" data-slug-hash="qqMQzy" data-default-tab="css,result" data-user="dbridgman" data-embed-version="2" data-pen-title="HTML5 Video Background Example" class="codepen">See the Pen <a href="http://codepen.io/dbridgman/pen/qqMQzy/">HTML5 Video Background Example</a> by Dane (<a href="http://codepen.io/dbridgman">@dbridgman</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

## The catches
It is hard to disagree that the effect is really nice, and it's so surprising just how easy it is to achieve. However these things do come at a cost, and some things need to be taken into consideration:

* Though background video is the flavour of the month, it's important to consider whether a background video is really going to support or add to the content you have on the page. Steve the plumber probably doesn't need a background video of tree blowing in the wind.
* As a front end I want my site builds to be high performing, and video has the potential to be VERY bulky. So making sure videos are nicely compressed, without trading off the picture quality of the video too much is exceedingly important. That way we can ensure load times are kept at a minimal, and we're being considerate to people on their mobile devices.
* Snazzy CSS and Javascript will not save a poor quality video.
* For those folks that cannot run the video it's worth having fall backs, for example it's a good idea having a background image on standby in case the video fails to load.

Overall I think if the use of HTML5 video is well executed it can be a real neat addition to a page, and the fact its so malleable with CSS and Javascript makes it super straight forward to use.
