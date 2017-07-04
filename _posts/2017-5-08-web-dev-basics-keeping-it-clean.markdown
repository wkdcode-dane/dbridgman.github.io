---
layout: post
title:  "Web Dev Basics - Keeping It Clean"
meta-description:  "Today I look into some quick easy tips for beginners on how to keep your projects tidy."
date:   2017-06-06
---

**Throughout my time working in web development I've grown a strong appreciation for working with code that is nicely structured and easy to understand. Making something that works is one thing, but there are a whole host of issues when general house keeping is an after thought. This is what I'm going to talk about today, and is something I've been wanting to write about for quite a while now.**

One thing I never really thought about was how much house keeping is ignored in a lot of beginner tutorials, and I think it's something that should really be drilled into juniors from the get go to ensure no bad habbits get embedded into the brain. There are a number of reasons why keeping a tidy project could benefit your practice, not only will this provide other developers or team members an easier time when looking at your work, but you'll find some vast benefits to take away yourself. Some key points for me are:

* It saves vast amounts of time, since nicely organised code makes everything easier to find. Not only for yourself, but other developers and team members.
* If you need to seek help, then a tidy code structure will make it easier for helpers to diagnose your problem.
* It's all in the name, if things are correctly structured and well named, then there is no ambiguity as to what is doing what. Whether it's a class name or a function, it is what it is.
* If a project starts to expand it makes your codebase vastly more maintainable.
* Prevents hair loss.

## A few handy points

My very first job in web saw me making modifications to existing websites, and throughout that time I was subjected to both ends of the spectrum. Sometimes some sites could be totally indecipherable, while others were a joy to work with. In both circumstances I like to think I learnt a lot in terms of do's and dont's, and I wanted to share a couple of handy basic points picked up along the way. I appreciate some of these points really are only just scratching the surface, and you could do an entire blog post on just a single one of these points in some cases - but hopefully gliding over some of these things will put the idea out there for any juniors out there.

## Structure and name your project considerately

There are thousands of different ways to structure your projects, many such ways dictated by the platform or framework you may be using. However it's important to consider laying out your files in as logical manner as possible, whether it's a SCSS file or a React component, generally these should be sectioned out into a neat and tidy structure with a name that is helpful. An example of this would be sectioning React components into their own directories, and nesting files and directories into structures that make sense. Consider the below:

{% highlight html %}

├── components
│   ├── Header
│   │   ├── Header.jsx
│   │   ├── header_test.jsx
│   │   └── index.js
│   ├── Footer
│   │   ├── Footer.jsx
│   │   ├── index.js
│   │   └── footer_test.jsx
│   └── index.js
├── index.jsx

{% endhighlight %}

A more logical, tree like structure such as the above would save a lot of heartache in the long run since it cuts out any ambiguity as to where and what each file is doing. Lets not also forget that being tidy like this is going to make your project easier to handle at larger scales, and makes everything modular out of the box. It's clear that everything within the 'components' folder is a component, and everything within the 'Header' folder is apart of the Header component. No matter the project always try to keep your structure as tidy as you can around the confines of what you're working with, whether it's a single page application, a portfolio site, a Wordpress site and so on.

## Name your functions considerately

I'd like to think this is going to be a point that is more or less a given, we've all been in situations where you jump into a project you haven't looked at in a few months and realised you've no idea what is going on. Little things like being considerate when declaring variables and functions can be a godsend, now I appreciate my example is just skimming the surface - but consider the below:

{% highlight javascript %}

const kittensAreCool = {
    sanityLevel: '-900',
    x: 'Insane'
} 

function whatAreWeTalkingAbout() {
    if(kittensAreCool.sanityLevel < 0 ) {
        kittensAreCool.x = "Insane";
    } else {
        kittensAreCool.x = "My mind is zen";
    }
    console.log(kittensAreCool.x);
}

whatAreWeTalkingAbout();

{% endhighlight %}

The above doesn't really give us a clear cut idea of what exactly our function is referencing on the page or doing, from a very basic level we can see it's checking an objects property and setting another property within the object based on it's outcome. But how does it all fit together? Everything is too abstract.

Now lets make a few adjustments to represent what we're trying to do:

{% highlight javascript %}

const danesBrain = {
    sanityLevel: '0',
    status: 'Insane'
} 

function sanityCheck() {
    if(danesBrain.sanityLevel < 1 ) {
        danesBrain.status = "Insane";
    } else {
        danesBrain.status = "My mind is zen";
    }
    console.log(danesBrain.status);
}

sanityCheck();

{% endhighlight %}

A few simple adjustments and suddenly everything is a lot less abstract, and there is no real confusion over what exactly is being spewed out and controlled by our script. Being thoughtful over naming conventions in cases such as this can be a huge time and sanity saver later down the line. Apologies for the silly example, can you tell I'm a little bit bitter about this particular point?

## Leave short and concise comments where needed

This one would probably get mixed responses from many of you, especially if you're pretty clean in general with your code. However a lot of benefits can be found in leaving short and concise comments where needed, particularly when you might want to section something off.

A great example would be a Wordpress functions file, more often than not with more complex Wordpress builds your functions file can end up a little like a jungle. I've always found it handy to drop a comment to label blocks of code and what they're doing for any unsuspecting developers that may be pouring over the file or working on the site in the future. Just labelling your enqueued scripts, your menus, custom post types, and so on... can make everything a lot clearer to onlookers.

The same principle could be applied if you're kicking around with script files that may house lots of different forms of functionality in a single file. Adding labels using comments can be a huge help later down the line, sometimes even small hints can help a lot. We could use the code from a second ago as an example, if it's in a big file with lots of other things just throw a label on it:

{% highlight javascript %}

// Sanity Check For Danes Brain

const danesBrain = {
    sanityLevel: '0',
    status: 'Insane'
} 

function sanityCheck() {
    if(danesBrain.sanityLevel < 1 ) {
        danesBrain.status = "Insane";
    } else {
        danesBrain.status = "My mind is zen";
    }
}

sanityCheck();

{% endhighlight %}

In a nutshell though, don't go mad with comments - use them sparingly and only when they're needed, if something is really obvious it probably doesn't need pointing out. We don't need a life story or an essay, just a simple note can make a world of difference!

## Correctly format and indent your code

This is perhaps one of the most commonly unconsidered points on the list, and probably the most wide spread from my experience. Writing clean code can take some real training if left to go wild for an extended period of time, I've seen countless bad habbits pop up over the years, and I've been as guilty as many in the past with my formatting (My excuse is Wordpress spaghetti code poisoning my judgement). I find this is something you get infinitely better at if you work within a team, people WILL tell you off if you're sloppy. Bad formatting can cause nightmares and mess, and bugs love to hide in both of those things usually which makes it difficult for your bug spray to attack.

Indenting is hugely important for readability of your code, it's much easier to digest everything in the file if it's done correctly. On a very basic level if you have items nested inside something, it probably needs indenting. Consider some basic menu markup below:

{% highlight html %}

<nav class="navigation" role="navigation">
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about-me">About Me</a></li>
        <li><a href="/blog">Blog</a></li>
        <li><a href="/contact">Contact</a></li>
    </ul>
</nav>

{% endhighlight %}

Indentation makes everything easier to read and debug, regardless as to whether you may be uglifying your code or not - in production it's imperative to keep things well indented to make things easier to maintain. It makes elements much more apparent where they're sitting in accordance to everything else around it, if you're not correctly indenting the lines tend to blur and your code will fast become difficult to understand and debug.

Though the example above is basic HTML markup, the same principles can be applied to whatever language you're writing in. Particuluarly when you're dealing something like Javascript, scope can be a total minefield when you're learning, and something as simple as indentation can do a great deal in making your life easier when dealing with nested functions.

## Stay vigilant 

While the points I've mentioned above are pretty vague in some cases, and I'd imagine a lot of you do these already as second nature - it never hurts to drill a point home. There are always going to be differing opinions across the community in terms of what could be considered best practice, but the best way to make sure you don't have any hurt coming your way is to stay vigilant with your code. If you're stepping into a new job make sure you probe your new peers on in house standards and nuances, or if you're doing something that may feel a little bit wrong it never hurts to ask someone or do some digging yourself on the subject. In the end following these principles will ensure you keep a thick head of hair, and other developers working with you will be happy bunnies. 

## Sharing is caring

Had any horrible experiences you've learnt from in the past? Picked up any handy hints along the way that are worth sharing? I'd love to hear some of your experiences and tips below.

In the meantime, happy developing!

