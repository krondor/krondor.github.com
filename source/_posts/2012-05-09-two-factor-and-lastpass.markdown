---
layout: post
title: "two factor and lastpass"
date: 2012-05-09 12:43
comments: true
categories: [passwords, security, lastpass, mfa, blog]
---
You need multi-factor authentication.  Passwords are no longer good enough.  

{% pullquote %}
How secure is your password?  If we've learned anything over the years on the
 Internet it's this. {"You shouldn't trust your password.  It has probably been
 compromised."}  Even if it hasn't, you might as well treat it as such.  These
 are strong words, but it's not an illogical stance to take.  How good are your
 password practices?  Do you mix case, use alphanumeric characters, spaces, or
 symbols?  Is your password over 14 characters long?  Do you change them on a
 regular basis?  Do you recycle them?  Is it based on a dictionary word or
 known item from your life?
{% endpullquote %}

Chances are you are not doing at least a few of the points above.  Which is why
 for years I've been an advocate of password managers.  I'm presently using
 [LastPass](http://lastpass.com), which is the genesis for this post.  I've
 used quite a few of these in my day (most recently [kwallet](http://docs.kde.org/stable/en/kdeutils/kwallet/index.html)
 and [KeePassX](http://keepassx.org).  Some are better than others, but almost
 any is better than nothing.  LastPass, however, has particularly impressed me.
  So what makes it so special, and how can it help keep us more secure?

<!-- more -->

##Why LastPass?##

{% img left /images/LastPassLogo329x40.png %}

Like any good password manager, LastPass holds the keys to your life in an
 encrypted vault.  You manage entries in the vault and lock it with a master
 password.  The vault can generate random passwords for you and assign those
 to entries.  This is all par for the course as these things go, and don't
 necessarily stand out on their own.  

So what makes LastPass so good;

-   Cloud Synchronization
-   Client Side Encryption
-   Multi-factor Authentication Support
-   One Time Use Passwords
-   Browser Plugin Support (Chrome/Firefox/Internet Explorer/Opera/Safari/Others)
-   Multiple Platform Support (Android/iOS/Linux/OSX/Windows/Others)
-   More Than Passwords (Form Data/Notes)
-   Price (LastPass is free for use outside of mobile clients)
-   Password Sharing with Friends
-   Import/Export Utilities
-   Phishing Protection

In particular, the cloud synchronization has been immense.  Knowing that all my
 computers can utilize the same password vault, across operating systems and
 browsers has been huge.  With that in place you no longer need to remember
 your logins, and with that you can generate random passwords uniquely for all
 sites.  Now you've compartmentalized your exposure.  If someone were to
 compromise the account you made on that one blog about snorkeling, you wouldn't
 be at risk that they could use that same password for your bank.  You've
 mitigated your risk just in this one act.  

So that's great but this online synchronization sounds like it might not be
 that great an idea.

###Cloud Synchronization###

LastPass syncs your vault to their online service.  

That is a scary statement, and immediately had me worried when I saw the
 service.  How can I trust that their backend is secure?  If it worries you to
 have your password vault propagated across the Internet, don't worry it means
 your self preservation instinct is working correctly.  LastPass works around
 this basic issue of trust through the use of a [salted hash](http://en.wikipedia.org/wiki/Salted_hash).
  Effectively this means that passwords and form data you populate into your
 vault, are encrypted client side and only the resultant hash with salt is sent
 to their online system.  LastPass doesn't know the vault contents of its users
 only the hashes. 

This is an important point because it nullifies one of the biggest issues with
 password based authentication.  The password storage.  You could be the poster
 child for security password best practices, and when the website you're
 visiting gets hacked (and left your password cleartext in their database),
 your password has been compromised.  This sounds trivial, but you might be
 surprised [how](http://www.codinghorror.com/blog/gawker-hack-release-notes.html)
 [many](http://www.reddit.com/comments/usqe/reddits_streak_of_bad_luck_continues/cuugl)
 [popular](http://www.itworld.com/security/249460/hacked-microsoft-online-store-saved-passwords-plain-text)
 sites haven't learned their lesson about storing clear text passwords.  I
 suppose I should also elaborate that the use of a salt is key here.  Even
 passwords that are hashed are vulnerable to [rainbow tables](http://en.wikipedia.org/wiki/Rainbow_table),
 and these are increasingly pre-generated for the taking.  The salt nullifies
 this leaving the stolen password vault only vulnerable to the venerable (and
 much more time consuming) offline dictionary attack.

{% blockquote Steve Gibson, http://www.youtube.com/watch?v=r9Q_anb7pwg&feature=player_embedded Security Now 256: LastPass Security %}
"This thing is secure every way you can imagine. And it's simple,"
{% endblockquote %}

So that's a pretty bold statement, and given the context of the conversation on
 that linked episode I wouldn't put too much weight in that.  However,  it does
 seem nice that LastPass has a good level of industry analysis and commenting
 by security folks.  It's not open source, and that takes away a degree of
 trust in my mind, but the model does seem sound.  

Now I should point out that you can accomplish similar ends with other solutions
 like KeePassX and Dropbox.  However, there is a level of trust in your
 synchronization mechanism and an ease of use factor to consider.  Dropbox, in
 particular, hasn't had a stellar [security record](http://blog.dropbox.com/?p=821). 
 There are other options (some of them [more secure](https://www.box.com/)),
 but with them you may incur costs or complexity which directly impacts the
 platforms and sync options you have.  

I could probably go on, but let's get to the next point. 

###Multi-factor authentication###

The security mechanisms in place around your password vault are all well and
 good, but they're not enough.  The vault can still be attacked, and now that
 it's online and synchronized between all the computers and mobile devices you
 won means its **much** more exposed.  In fact, a more likely hacking avenue,
 might not be a dictionary attack against your vault.  It's easy to become lazy
 and security can be annoying.  It's a PITA to always have to authenticate to
 your vault, and it's really easy to check that remember my password button. 
 Sure you've got a password on your workstation, laptop, and phone right? 
 Maybe, it's not the remember my password button, but the keylogger on the
 malware you didn't know you had?  You've patched [flash](http://www.forbes.com/sites/adriankingsleyhughes/2012/05/06/emergency-flash-update-fixes-security-vulnerability-used-to-hijack-windows-pcs/)
 recently right?

There needs to be another barrier on your online identity, and LastPass has you
 covered.  [Multi-factor authentication](http://en.wikipedia.org/wiki/Multi-factor_authentication)
 provides that second level of authentication to make the system that much
 harder to compromise.  LastPass has included support for a variety of
 additional authentication mechanisms.  Yubikey, Google Authenticator, and USB
 key options exist.  The idea here is that even if your password is compromised
 attackers would still need to enter the second form of authentication
 (usually a numeric PIN that changes every 60 seconds), that old adage something
 you have and something you know.  

{% img /images/googleauth_authenticate.png %} 

Multi-factor can be a pain, but it's an additional piece of mind that puts a
 significant barrier on your identity theft.  If you look at the most
 significant hacking targets (government, banking, online game platforms
 (steam, battle.net)) you'll note a generally strong uptake of multi-factor
 authentication.  This is because it is quite effective (although that didn't
 stop the [RSA hack](http://www.schneier.com/blog/archives/2011/08/details_of_the.html),
 but that's a different discussion).  [Mobile authenticators on smartphones](https://code.google.com/p/google-authenticator/),
 [USB keys](http://helpdesk.lastpass.com/security-options/sesame-multifactor-authentication-with-a-usb-thumb-drive/) (*premium feature*),
 [NFC](http://www.yubico.com/yubikey-neo), and the like have done a great deal
 to make this accessible and easy to live with for everyday usage.  A word of
 caution, you'll note in the screenshot the checkbox to **not require** two
 factor for this computer.  You can get into the same *remember my password*
 quandary with indiscriminate checking of that box.  

What's the point of two factor if you disable it?

###Conclusion###

{% img right /images/tryit.jpg %}

So I could go on and on about the other nifty things.  Sharing passwords with a
 friend/spouse/associate without actually giving them the password or access to
 the vault.  How about, one time use passwords for that time you want to see
 your vault at Starbucks, but don't trust the computer to not log your
 keystrokes?  Or how about the on screen keyboard for your password entry
 (again fighting keyloggers).  Instead, I'll just leave it to this.

**LastPass is free and good.  Try it, you'll like it!**
