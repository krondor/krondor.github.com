---
layout: post
title: "two factor and lastpass"
date: 2012-05-09 12:43
comments: true
published: false
categories: [passwords, security, lastpass, mfa, blog]
---
You need multifactor authentication.  Passwords are no longer good enough.  

{% pullquote %}
How secure is your password?  If we've learned anything over the years on the Internet its this. {"You shouldn't trust your password.  It's probably been compromised."}  Even if it hasn't, you might as well treat it as such.  These are strong words, but it's not an illogical stance to take.  How good are your password practices?  Do you mix case, use alphanumeric characters, spaces, or symbols?  Is your password over 14 characters long?  Do you change them on a regular basis?  Do you recycle them?  Is it based on a dictionary word or known item from your life?
{% endpullquote %}

Chances are you are not doing at least a few of the points above.  Which is why for years I've been advocate of password managers.  I'm presently using <a href="http://lastpass.com">LastPass</a>, which is the genesis for this post.  I've used quite a few of these in my day (most recently <a href="http://docs.kde.org/stable/en/kdeutils/kwallet/index.html">KWallet</a> and <a href="http://keepassx.org">KeePassX</a>).  Some are better than others, but almost any is better than nothing.  LastPass, however, has particularly impresed me.  So what makes it so special, and how can it help keep us more secure?

<!-- more -->

{% img /images/LastPassLogo329x40.png %}

Like any good password manager, LastPass holds the keys to your life in an encrypted vault.  You manage entries in the vault and lock it with a master password.  This is all par for the course as these things go, and don't necessarily stand out on their own.  However, the means with which LastPass does this does differ significantly from many password managers.  LastPass syncs your vault to their online service.  

That is a scary statement, and immediately had me worried when I saw the service.  How can I trust that their backend is secure?  If it worries you to have your password vault propagated across the Internet, don't worry it means your self preservation instinct is working correctly.  LastPass works around this basic issue of trust through the use of a <a href="http://en.wikipedia.org/wiki/Salt_%28cryptography%29">salted hash</a>.  Effectively this means that passwords and form data you populate into your vault, are encryptd client side and only the resultant hash with salt is sent to their online system.  LastPass doesn't know the vault contents of its users only the hashes.  

This is an important point because it nullifies one of the biggest issues with password based authentication.  The password storage.  You could be the poster child for security password best practices, and when the website you're visiting gets hacked (and left your password cleartext in their database), your password has been compromised.  This sounds trivial, but you might be suprised <a href="http://www.codinghorror.com/blog/gawker-hack-release-notes.html">how</a> <a href="http://www.reddit.com/comments/usqe/reddits_streak_of_bad_luck_continues/cuugl">many</a> <a href="http://www.itworld.com/security/249460/hacked-microsoft-online-store-saved-passwords-plain-text">sites</a> haven't learned their lesson about storing clear text passwords.  

{% blockquote Steve Gibson, http://www.youtube.com/watch?v=r9Q_anb7pwg&feature=player_embedded Security Now 256: LastPass Security %}
"This thing is secure every way you can imagine. And it's simple,"
{% endblockquote %}

So that's a pretty bold statement, and given the context of the conversation on that linked episode I wouldn't put too much weight in that.  However,  it does seem nice that LastPass has a good level of industry analysis and commenting by security folks.  It's not open source, and that takes away a degree of trust in my mind, but the model does seem sound.  I could probably go on, but let's get to the next point.  Multi-factor authentication.
