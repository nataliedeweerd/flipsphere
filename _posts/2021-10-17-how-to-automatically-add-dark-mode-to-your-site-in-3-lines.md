---
layout: post
title: "How to automatically add dark mode to your site in 3 lines"
subtitle: "A super quick and easy way of instantly adding a dark mode to your website."
date: 2021-10-17
---

``` css
@media (prefers-color-scheme: dark) {
    * {filter:invert(1);}
}
```

The result won't be perfect (in fact, it'll probably look downright awful), but it gives you a great starting point to then pull out individual colours and rebuild the CSS how you want!

The `@media (prefers-color-scheme:dark){ ... }` is all you need to automatically trigger dark mode styling on your site if the user has set their browser to dark mode.

This is how I created the new dark mode on my blog. Started with the `filter:invert(1);` trick, picked out the colours manually in the inspector that worked, and slowly tweaked the rest. 