---
layout: post
title: "chrome frame"
date: 2012-02-09 15:27
comments: true
categories: [ocotopress, chromeframe, blog, howto] 
---
So having spent some time fumbling around in <a href="http://octopress.org">octopress</a>, I've made my first modification.  Internet Explorer is a constant source of pain when theming websites.  As this is my personal blog there isn't really a reason to be particularly friendly to Internet Explorer, and so I thought why not prompt my visitors to install <a href="http://code.google.com/chrome/chromeframe/">Chrome Frame</a>.

Chrome Frame effectively replaces the rendering engine of IE with Google Chrome through a plugin for IE.  In effect users who install it are now running Chrome, and as such are treated with properly working CSS/HTML5/JS support.  Which now means they can see my nicely rendered 3D logo all in CSS courtesy of <a href="http://www.markdott.com/2011/01/05/3d-text-using-just-css/">Mark Otto</a>.  Wondeful, but how to get my visitors to install Chrome Frame? 

Once Chrome Frame has been installed the user-agent header can report its presence.

``` apache Chrome Frame User-Agent Example
Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; chromeframe/11.0.660.0)
```

Given that we can detect if Chrome Frame is installed it's possible to selectively prompt visitors to install it for IE if they haven't done this already.  There's a great guide on the process on the Chromium site <a href="http://www.chromium.org/developers/how-tos/chrome-frame-getting-started">here</a>.  However, I didn't want to just go about pasting the scripts snippet into my HTML body here.  I mean that's why I'm using Ocotpress and not just native HTML right?  Let's programatically decide if we should push our IE friends toward the Chrome light.  

So how to inject the Chrome Frame javascript in Octopress?  Let's begin with a configuration directive to test against in our _config.yml.  

``` yml _config.yml chrome frame directive
# Chrome Frame Prompt
chromeframe: true
```

Now that we have a clause to test against Octopress can decide on whether or not to build the chrome frame code into the site.  The only piece left was to decide where the code should recide.  Octopress is pretty good at maintaining a custom directory structure for modifications to the base.  It's a good idea to keep that structure so updates to the core are easier to maintain.  Head.html seems to be the logical place for onload scripts to me, so I made my custom changes there.

``` bash chrome frame custom html file location
/home/myuser/octopress/source/_includes/custom/head.html
```

Now I declare when the code should be included given our config.yml directive using <a href="http://liquidmarkup.org>Liquid</a> markup syntax with an if block.

``` liquid _config.yml option if block
{% if site.chromeframe %}
some code
{% endif %}
```

I paste in the chrome frame installation script from the Chromium example linked above and modify it for my needs, and we're good to go. I really didn't change much.  I opted to use overlay mode for the prompt because I'm not quite sure where I'd like to inject it inline.  The only issue with overlay (besides annoyance to my visitors), is that it doesn't seem to work on IE7 and earlier.

{% include_code [final customized head.html with modifications] head.html %}

So far so good, now we can deploy and test;

``` ruby build and deploy site changes
rake generate
rake deploy
```

Success!  Now if only they'd install it (or even better just get a full Chrome or Firefox browser in the first place).
