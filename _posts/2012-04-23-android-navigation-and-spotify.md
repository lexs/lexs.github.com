---
layout: post
title: Android navigation and Spotify (with friends)
comments: true
---

The newly released [beta](http://www.spotify.com/se/blog/archives/2012/04/19/new-android-preview/) of the Spotify Android client is a big step forward but still retains some oddities from the old version, like having settings as a separate view. It also adopts the sliding menu pattern coined by the iOS Facebook version. 

![Facebook]({{ site.url }}/images/facebook-ios.jpeg)
![Spotify]({{ site.url }}/images/spotify-menu.png)

This pattern is natural to iOS users due the use of overscrolling and for the fact that users are accustomed to slide to reveal more options. On Android it is different, swipe should be used to scroll between content, and in the case of list views, dismiss items. This makes this pattern alien to Android users.

I find it odd that Spotify adopted this pattern when the rest of the application feels very much like Android. Perhaps this is to unify with an upcoming iOS refresh. While their implementation is very smooth (the same can not be said for Facebook's) I hope they can make it more Android.

A problem that is common for iOS adaptations is that the back button can be used for navigating between views, for example like above or when using tabs. The [Android Design Guidelines](http://developer.android.com/design/index.html) has the following to say about this:

> Changing view options for a screen does not change the behavior of Up or Back: the screen is still in the same place within the app's hierarchy, and no new navigation history is created.

Spotify, Facebook and Instagram all fail here in different ways. Spotify and Facebook use the pattern above but does not make it clear to the user how it affects the back stack. They simply push the selected view on top without any animation. This leads to a continuously expanding activity stack making it awkward to navigate back. Instagram on the other hand uses tabs but still pushes the views on the stack instead of replacing them.

The guidelines suggest using a spinner for this kind of navigation (aka collapsed tabs). This is what most of the platform apps do, for example Gmail, Calendar and Maps. What is not clear though is how the back stack should be treated.

![Gmail]({{ site.url }}/images/android-gmail.jpeg)
![Maps]({{ site.url }}/images/android-maps.png)

But given how it's implemented in Gmail vs Maps, it's pretty clear how it should be handled. In Gmail the mail list is the starting point of the app, the views in the spinner filter this list but it's still a list of mails. Maps on the other hand uses the spinner for different views, much like Spotify. It still pushes views on the stack but when the user selects the main entry point, "Map" here, they clear the back stack and return to the first view. Tapping back will not exist the app.

Spotify could easily adopt the pattern used by Maps by using a spinner and clearing the back stack when "Playlists" is selected. Search and settings should go in the regular action area leaving four items, which is less than Maps has. Facebook has more items but could show the most common like Gmail does with *"Show all labels"*. They should also provide animations for showing the user how this affects the back stack, this chould be done by using simply using activities.

**Interesting remark:** Spotify uses the Action Bar compatibility [sample](http://developer.android.com/resources/samples/ActionBarCompat/index.html) provided by Google instead of the more powerful [ActionBarSherlock](http://actionbarsherlock.com/).

In conclusion: Spotify and others, please switch to a spinner for view navigation.

**UPDATE:** I wrote a new [blog post](/2012/06/01/slide-out-navigation-done-better/) which details another implementation of the sliding menu.