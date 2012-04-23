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

Spotify, Facebook and Instagram all fail here. Spotify and Facebook use the pattern above while Instagram sticks with tabs but still manages to get it wrong.

The guidelines mention using a spinner in the action bar for this kind of navigation. This is exactly what the platform apps do (Gmail, Calendar and others).

![Gmail]({{ site.url }}/images/android-gmail.jpeg)
![Calendar]({{ site.url }}/images/android-calendar.png)

Spotify could easily adopt this pattern. Search and settings should go in the regular action area leaving four items, which is less than Gmail has. Facebook has more items but could show the most common like Gmail does with *"Show all labels"*. The back button should also not go back to the last recent view but navigate up in the hierarchy.

**Interesting remark:** Spotify uses the Action Bar compatibility [sample](http://developer.android.com/resources/samples/ActionBarCompat/index.html) provided by Google instead of the more powerful [ActionBarSherlock](http://actionbarsherlock.com/).

In conclusion: Spotify and others, please switch to a spinner for view navigation.