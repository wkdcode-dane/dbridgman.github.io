---
layout: post
title:  "Dynamic Match Height Function With Vanilla Javascript"
meta-description:  "How to match element heights dynamically with vanilla Javascript"
date:   2017-07-19
---

**Dynamically matching the heights of multiple page elements is a problem every web developer will encounter at one point or another, like many other developers I have reached for third party jQuery plugins before. However I decided to throw the plugins in the bin and come up with my own solution with nothing but a little bit of Javascript.**

Many of you will be shouting at the screen right now saying 'Dane! We can just use flexbox now mate, the web is moving on!', however I would argue there are still cases where using just CSS will not quite solve your problems for you. Especially if these elements are at different points of the page.

##The Code

Please bear in mind my example contains ES6 syntax, so it'll only work in IE11+ unless you pull Babel out of your toolbox - or switch a few bits out yourself. 

My main aim was to create a reusable function that I could parse through a class, and throw through an event listener without any problems. This just means we can recalculate the heights should the screen get smaller or larger, or we want it to trigger at a certain point.

{% highlight javascript %}

function matchHeight(elems) {

    const items = document.querySelectorAll(elems)
    const arrayItems = Array.prototype.slice.call(items)
    let maxHeight = 0

    arrayItems.forEach(function(e) {
        
        e.style.minHeight = "0"
        let height = e.offsetHeight

        if (height >= maxHeight) {
            maxHeight = height
        }

    })

    arrayItems.forEach(function(e) {

        e.style.minHeight = maxHeight + "px"
        e.style.boxSizing = "border-box"
        
    })    
}

{% endhighlight %}

##Breaking It Down

So to start we need to grab all the elements that have been fed into the function, then push them into an array to allow us to loop through them with ease. Then of course declare a `maxHeight` variable for us to tap into later.

{% highlight javascript %}

    const items = document.querySelectorAll(elems)
    const arrayItems = Array.prototype.slice.call(items)
    let maxHeight = 0

{% endhighlight %}

The next part is the fun bit, we then start a `forEach` loop in which we cycle through each of our selected elements and measure their heights. A key thing to note is before we do the measuring you'll notice the `e.style.minHeight = "0"`, this is essentially setting the minimum height of the element to 0 to allow us to measure the actual current height of the element. This may seem odd, but consider if you repeat the script again when the window resizes - the element's heights will be stuck at the point in which it's height was the largest, which is no good if it needs to resize to a smaller size.

We then measure the height via `offsetHeight` and check if it's higher than the maxHeight we set earlier, if thats the case - the current maxHeight is set to the height we measured.

{% highlight javascript %}

    arrayItems.forEach(function(e) {
        
        e.style.minHeight = "0"
        let height = e.offsetHeight

        if (height >= maxHeight) {
            maxHeight = height
        }

    })

{% endhighlight %}

After that all we then need to do is set the `minHeight` of the elements by looping through them again and applying our new minimum height as our newly updated maxHeight variable. One thing you'll notice is I am also setting our `box-sizing` of the element to `border-box` as a precaution. Without it the `offsetHeight` will not correctly take into consideration our padding and borders when measuring the height of the elements, and the sizing adjustments will not work as we need it to.

{% highlight javascript %}

    arrayItems.forEach(function(e) {

        e.style.minHeight = maxHeight + "px"
        e.style.boxSizing = "border-box"
        
    }) 

{% endhighlight %}

Lastly all that is left to do is execute the function by parsing through the class of the objects we wish to match up, and passing it through an event listener. Below I have done it on page load, as well as when the window resizes.

{% highlight javascript %}

    window.addEventListener('load', function() {
    matchHeight('.element')
    });
    window.addEventListener('resize', function() {
    matchHeight('.element')
    });

{% endhighlight %}

If you want to see it in action I've added it to <a href="https://codepen.io/dbridgman/pen/yXdXXG?editors=1111" target="\_blank">Codepen</a> for your perusal!

Pretty straightford huh? If you're after super backwards compatibility tread carefully with the code above and make sure you run it through Babel, or change the syntax to something a little more IE friendly. This was mainly done as a proof of concept, but it goes to show that you really can achieve a really lightweight solution and not really have to rely on some overly bulky jQuery plugins to do the job.

Enjoy!
