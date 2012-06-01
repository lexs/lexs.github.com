---
layout: post
title: Slide-out navigation done better
comments: true
---

My last [blog post](/2012/04/23/android-navigation-and-spotify/) was about the sliding menu pattern that several apps are now using. My main critisism was that the pattern in its current form felt didn't feel very much Android, mainly because how it treats the back stack.

After this the new [Google+ app](https://play.google.com/store/apps/details?id=com.google.android.apps.plus) was released showcasing this same pattern (though they call it a ribbon menu). Their implementation differs from others because the action bar remains in place. Only the menu itself actually moves. They also only show the menu on the main screens, using the regular up action for sub-activities.

![Google+ menu]({{ site.url }}/images/google-plus-menu.png)
![Google+ post]({{ site.url }}/images/google-plus-post.png)

I quite liked how the let the action bar remain in place but I disliked that they didn't slide the content. They also used the same right caret which is used for up, though this was probably just a mistake. They main difference about their implementation is how they handle the back stack though, they only display the menu on top level activities. This makes the pattern feel like an evolution of the [dashboard pattern](http://www.androiduipatterns.com/2011/02/ui-design-pattern-dashboard.html).

I was in the process of developing an app for [Delicious](http://www.delicious.com/) which used spinner navigation but the Google+ implementation made me think again. I felt that you could combine their implementation with others to get the best of all worlds. This is what I came up with:

* Slide content (Facebook/Spotify)
* Don't slide the action bar (Google+)
* Use different icon for menu (Facebook/Spotify)
* Display menu on main acitivities only (Google+)
* Backstack that makes sense (Google+ comes close)
* Gesture support (Spotify)

Based on these points I implemented the pattern in my app. I used an [ActionMode](http://developer.android.com/reference/android/view/ActionMode.html) for transforming the action bar, this also gives you automatic handling of the back button for closing the menu.

![Menu hidden]({{ site.url }}/images/delicious-app.png)
![Menu shown]({{ site.url }}/images/delicious-menu.png)

The app itself is pretty simple but the menu should scale well. The back stack remains simple when only main activities can display the menu. Here is a simple flow chart of the app:

![Back stack]({{ site.url }}/images/delicious-back-stack.png)

The app is fully open source over at [Github](https://github.com/lexs/android-delicious) and it also available at the [Play Store](https://play.google.com/store/apps/details?id=se.alexanderblom.delicious).